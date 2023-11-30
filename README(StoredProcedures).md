# Store Prosedürler 
### 1.CategoryListWithSubCategories

```
CREATE PROCEDURE CategoryListWithSubCategories
AS
BEGIN
WITH CategoryHierarchy AS (
	SELECT
		Id,
		Name,
		IsActive,
		MainCategoryId,
		CAST(Name as VARCHAR(MAX)) AS Hierarchy
	FROM
		Categories
	Where MainCategoryId is Null

	UNION ALL

	Select
		c.Id,
		c.Name,
		c.IsActive,
		c.MainCategoryId,
		CAST((ch.Hierarchy + '>' + c.Name) AS VARCHAR(MAX)) as Hierarchy
	From
		Categories c
		INNER JOIN CategoryHierarchy ch
		on ch.Id=c.MainCategoryId
)

SELECT Hierarchy FROM CategoryHierarchy where IsActive=1
END
```

### 2.CreateSeller

```
CREATE PROCEDURE CreateSeller
	@name VARCHAR(350),
	@address VARCHAR(MAX),
	@taxIdentityNumber CHAR(10),
	@identityNumber CHAR(11),
	@taxDepartmentId INT,
	@webSite VARCHAR(MAX),
	@phoneNumber VARCHAR(MAX),
	@email VARCHAR(500),
	@userName VARCHAR(150),
	@password VARCHAR(MAX)
AS
BEGIN
	SET @phoneNumber= CAST(REPLACE(@phoneNumber,'','')as VARCHAR(20));
	SET @userName= REPLACE(@userName,'','');
	SET @userName=UPPER(@userName);
	DECLARE @salt UNIQUEIDENTIFIER=NEWID();
	DECLARE @hashedPassword VARBINARY(8000)= HASHBYTES('SHA2_256',CONCAT(@password,CAST(@salt as VARCHAR(36))));

	DECLARE @RandomNumber INT;
	SET @RandomNumber = CAST((RAND(CHECKSUM(NEWID()))*899999)+100000 AS INT)

	INSERT INTO Sellers Values (
								@name,@address,@taxIdentityNumber,
								@identityNumber,@taxDepartmentId,
								@webSite,@phoneNumber,@email,@userName,
								@hashedPassword,@salt,0,@RandomNumber,
								GETDATE(),null,null,null,GETDATE(),null)
END

```

### 3.InsertCategory 

```
CREATE PROCEDURE InsertCategory 
	@Name VARCHAR(255),
	@IsActive bit,
	@MainCategoryId INT
AS
BEGIN
DECLARE @Path VARCHAR(MAX) = Replace(Replace(@Name,'',''),'','')

insert into Categories Values (@Name,@IsActive,@MainCategoryId,GETDATE(),null,@Path)
END
```

### 4.MainCategoryListByCategoryId

```
CREATE PROCEDURE MainCategoryListByCategoryId
      @categoryId AS INT=6
AS 
BEGIN
WITH CategoryHierarchy AS (
	SELECT
		Id,
		Name,
		IsActive,
		MainCategoryId,
		CAST(Name as VARCHAR(MAX)) AS Hierarchy
	FROM
		Categories
	Where
		Id = @categoryId

	UNION ALL

	SELECT
		c.Id,
		c.Name,
		c.IsActive,
		c.MainCategoryId,
		CAST((c.Name + '>' + ch.Hierarchy) AS VARCHAR(MAX)) AS Hierarchy
	FROM
		Categories c
		INNER JOIN CategoryHierarchy ch
		ON ch.MainCategoryId=c.Id
)

SELECT TOP 1 Hierarchy
FROM CategoryHierarchy
WHERE IsActive=1
Order by LEN(Hierarchy) Desc

END
```
