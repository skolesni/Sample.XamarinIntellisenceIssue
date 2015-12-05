Created in Visual Studio Professional 2015, Version 14.0.24720.00 Update 1

Step 1. Create Solution. File -> New -> Project -> Cross-Platform -> Blank App (Xamarin.Forms Portable); Name: Sample.XamarinIntellisenceIssue

Step 2. Update NuGet Packages. In Solution Explorer -> Right Click Sample.XamarinIntellisenceIssue -> Manage NuGet Packages for Solution... -> Updates -> Select all packages -> Update -> OK

Step 3. Add Common PCL project. (As this must be Profile78, the easiest way is to create a Xamarin Forms Class Library and remove unneeded dependencies)
    a. Add Project: In Solution Explorer -> Right Click Sample.XamarinIntellisenceIssue -> Add -> New Project... -> Cross-Platform -> Class Library (Xamarin.Forms); Name: Sample.XamarinIntellisenceIssue.Common -> OK
    b. Delete sample file: Delete file Sample.XamarinIntellisenceIssue.Common.cs
    c. Uninstall Xamarin.Forms: In Solution Explorer -> Right Click Sample.XamarinIntellisenceIssue.Common -> Manage NuGet Packages... -> Installed -> Select Xamarin.Forms -> Uninstall -> OK
    d. Create a new sample class: In Solution Explorer -> Right Click Sample.XamarinIntellisenceIssue.Common -> Add -> Class; Name: Class1 -> OK
    e. Change Class1 visibility to public: Open Class1.cs -> add "public" to the class definition
