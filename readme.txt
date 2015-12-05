Created in Visual Studio Professional 2015, Version 14.0.24720.00 Update 1

Step 1. Create Solution. File -> New -> Project -> Cross-Platform -> Blank App (Xamarin.Forms Portable); Name: Sample.XamarinIntellisenceIssue

Step 2. Update NuGet Packages. In Solution Explorer -> Right Click Sample.XamarinIntellisenceIssue -> Manage NuGet Packages for Solution... -> Updates -> Select all packages -> Update -> OK

Step 3. Add Common PCL project. (As this must be Profile78, the easiest way is to create a Xamarin Forms Class Library and remove unneeded dependencies)
    a. Add Project: In Solution Explorer -> Right Click Sample.XamarinIntellisenceIssue -> Add -> New Project... -> Cross-Platform -> Class Library (Xamarin.Forms); Name: Sample.XamarinIntellisenceIssue.Common -> OK
    b. Delete sample file: Delete file Sample.XamarinIntellisenceIssue.Common.cs
    c. Uninstall Xamarin.Forms: In Solution Explorer -> Right Click Sample.XamarinIntellisenceIssue.Common -> Manage NuGet Packages... -> Installed -> Select Xamarin.Forms -> Uninstall -> OK
    d. Create a new sample class: In Solution Explorer -> Right Click Sample.XamarinIntellisenceIssue.Common -> Add -> Class; Name: Class1 -> OK
    e. Change Class1 visibility to public: Open Class1.cs -> add "public" to the class definition

Step 4. Use Common PCL project in the Forms PCL project.
    a. Add Project Reference: In Solution Explorer -> Right Click Sample.XamarinIntellisenceIssue -> Add -> Reference.. -> Projects -> Solution -> Check Sample.XamarinIntellisenceIssue.Common -> OK
    b. Use Class1: Open App.cs -> In the end of constructor add "var class1 = new Class1();". Note that a reference "using Sample.XamarinIntellisenceIssue.Common;" is added
    c. Build Solution to ensure 0 errors (Check "Build succeeded" + "0 Errors" is reported in the Error List)

Step 5. Add XAML file to the Forms PCL project - this will break Intellisence
    a. Create a new XAML page: In Solution Explorer -> Right Click Sample.XamarinIntellisenceIssue -> Add -> New Item... -> Cross-Platform -> Forms Xaml Page; Name: Page1 -> OK
    b. Notice new erros:
        1. Error CS0234: The type or namespace name 'Common' does not exist in the namespace 'Sample.XamarinIntellisenceIssue' (are you missing an assembly reference?)	Sample.XamarinIntellisenceIssue	D:\Development\Samples\Sample.XamarinIntellisenceIssue\Sample.XamarinIntellisenceIssue\Sample.XamarinIntellisenceIssue\App.cs
        2. Error CS0246: The type or namespace name 'Class1' could not be found (are you missing a using directive or an assembly reference?)	Sample.XamarinIntellisenceIssue	D:\Development\Samples\Sample.XamarinIntellisenceIssue\Sample.XamarinIntellisenceIssue\Sample.XamarinIntellisenceIssue\App.cs
    c. Build Solution to ensure is succeeds, despite having errors (Check "Build succeeded" + "2 Errors" is reported in the Error List)

Step 6. Close Visual Studio and Open Again - this will produce another error:
    a. Close/Open Visual Studio
    b. Open Page1.xaml.cs file
    c. Notice new error: Error CS0103: The name 'InitializeComponent' does not exist in the current context	Sample.XamarinIntellisenceIssue	D:\Development\Samples\Sample.XamarinIntellisenceIssue\Sample.XamarinIntellisenceIssue\Sample.XamarinIntellisenceIssue\Page1.xaml.cs
    d. Build Solution to ensure is succeeds, despite having errors (Check "Build succeeded" + "1 Error" is reported in the Error List)

Step 7. Use Class 1 in the Page1.xaml.cs - this will produce more error:
    a. Use Class1: Open Page1.xaml.cs -> In the end of constructor add "var class1 = new Class1();". Note that a reference "using Sample.XamarinIntellisenceIssue.Common;" is added
    b. Create a new XAML page: In Solution Explorer -> Right Click Sample.XamarinIntellisenceIssue -> Add -> New Item... -> Cross-Platform -> Forms Xaml Page; Name: Page2 -> OK
    c. Notice new erros:
        1. Error CS0234: The type or namespace name 'Common' does not exist in the namespace 'Sample.XamarinIntellisenceIssue' (are you missing an assembly reference?)	Sample.XamarinIntellisenceIssue	D:\Development\Samples\Sample.XamarinIntellisenceIssue\Sample.XamarinIntellisenceIssue\Sample.XamarinIntellisenceIssue\App.cs
        2. Error CS0234: The type or namespace name 'Common' does not exist in the namespace 'Sample.XamarinIntellisenceIssue' (are you missing an assembly reference?)	Sample.XamarinIntellisenceIssue	D:\Development\Samples\Sample.XamarinIntellisenceIssue\Sample.XamarinIntellisenceIssue\Sample.XamarinIntellisenceIssue\Page1.xaml.cs
        3. Error CS0246: The type or namespace name 'Class1' could not be found (are you missing a using directive or an assembly reference?)	Sample.XamarinIntellisenceIssue	D:\Development\Samples\Sample.XamarinIntellisenceIssue\Sample.XamarinIntellisenceIssue\Sample.XamarinIntellisenceIssue\App.cs
        4. Error CS0246: The type or namespace name 'Class1' could not be found (are you missing a using directive or an assembly reference?)	Sample.XamarinIntellisenceIssue	D:\Development\Samples\Sample.XamarinIntellisenceIssue\Sample.XamarinIntellisenceIssue\Sample.XamarinIntellisenceIssue\Page1.xaml.cs
    d. Build Solution to ensure is succeeds, despite having errors (Check "Build succeeded" + "4 Errors" is reported in the Error List)
