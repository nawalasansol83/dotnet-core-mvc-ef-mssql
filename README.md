# .net core mvc with EF connecting to mssql running on RHE
<div>
for the application to un, we need to create the blogging database
</div>
<h3>
Create the database
</h3>
<div>
login to sql server using CLI and create the following database
</div>
<strong>
$ sqlcmd -S localhost -U SA -P ‘P@ssw0rd’
</strong>
<br/>
<h3>
Execute the following script
</h3>
<div>
CREATE DATABASE [Blogging];
</div>
GO
<br/>
USE [Blogging];
<br/>
GO
<br/>
CREATE TABLE [Blog] (
<br/>
    [BlogId] int NOT NULL IDENTITY,
<br/>    
    [Url] nvarchar(max) NOT NULL,
<br/>    
    CONSTRAINT [PK_Blog] PRIMARY KEY ([BlogId])
<br/>    
);
<br/>
GO
<br/>
CREATE TABLE [Post] (
<br/>
    [PostId] int NOT NULL IDENTITY,
<br/>
    [BlogId] int NOT NULL,
<br/>
    [Content] nvarchar(max),
<br/>
    [Title] nvarchar(max),
<br/>
    CONSTRAINT [PK_Post] PRIMARY KEY ([PostId]),
<br/>
    CONSTRAINT [FK_Post_Blog_BlogId] FOREIGN KEY ([BlogId]) REFERENCES [Blog] ([BlogId]) ON DELETE CASCADE
<br/>
);
<br/>
GO
<br/>
INSERT INTO [Blog] (Url) VALUES
('http://blogs.msdn.com/dotnet'),
('http://blogs.msdn.com/webdev'),
('http://blogs.msdn.com/visualstudio')
<br/>
GO
