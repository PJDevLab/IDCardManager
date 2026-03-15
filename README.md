ID Card Manager (ASP.NET MVC) - Overview

This workspace contains multiple related .NET solutions and projects centered around managing ID cards, users, and a points-based workflow.

1) IDCardManager_org (ASP.NET MVC / net8.0)
   - A full server-rendered MVC application for Admin/Distributor/User roles.
   - Core features:
     * JWT authentication (cookie-based)
     * Role-based dashboards (Admin, Distributor, User)
     * Template designer (canvas drag & drop)
     * PDF parsing + field extraction (iTextSharp)
     * ID card generation via HTML5 Canvas preview + ImageSharp rendering
     * Points system with atomic transactions
     * QR code / PDF support
   - Key folders:
     * Controllers/ (Account, Dashboard, Template, IDCard)
     * Services/ (JwtService, PdfParsingService, IDCardGeneratorService, PointsService)
     * Views/ (role-based UI, template designer, card generation pages)
     * Data/ (AppDbContext, migrations)

2) IDCardMasterAPI (ASP.NET Core Web API)
   - A separate API project likely used by a front-end client.
   - Includes controllers for Auth, Dashboard, User management.
   - Uses Entity Framework Core for data persistence.

3) IDCardMasterUI (ASP.NET Core Razor Pages / MVC)
   - A UI project that likely consumes the API (IDCardMasterAPI). 
   - Contains controllers and views for the front-end experience.

Running the main MVC app (IDCardManager_org):
  dotnet restore
  dotnet ef database update
  dotnet run

Points & ID Card Generation:
  - Each ID card generation consumes points (default templates cost 1 point).
  - If a user reaches 0 points, they must top up/increase their points before generating more ID cards.
  - Points are managed via the Distributor → User assignment workflow (Admin/Distributor can assign points).
