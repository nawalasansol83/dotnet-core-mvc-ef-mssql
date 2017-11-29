# .net core mvc with EF connecting to mssql running on RHE

Create the database
login to sql server using CLI and create the following database
$ sqlcmd -S localhost -U SA -P ‘P@ssw0rd’

<br/>
CREATE DATABASE [Blogging];
<br/>
GO
<br/>
USE [Blogging];
<br/>
GO
<br/>
CREATE TABLE [Blog] (
    [BlogId] int NOT NULL IDENTITY,
    [Url] nvarchar(max) NOT NULL,
    CONSTRAINT [PK_Blog] PRIMARY KEY ([BlogId])
);
<br/>
GO
<br/>
CREATE TABLE [Post] (
    [PostId] int NOT NULL IDENTITY,
    [BlogId] int NOT NULL,
    [Content] nvarchar(max),
    [Title] nvarchar(max),
    CONSTRAINT [PK_Post] PRIMARY KEY ([PostId]),
    CONSTRAINT [FK_Post_Blog_BlogId] FOREIGN KEY ([BlogId]) REFERENCES [Blog] ([BlogId]) ON DELETE CASCADE
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
