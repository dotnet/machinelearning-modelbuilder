# Troubleshooting for Model Builder
If troubleshooting does not solve the problem, please file a bug [here](https://github.com/dotnet/machinelearning-modelbuilder/issues/new?template=bug_report.md). 

## Dev Team Cannot Reproduce (no constant repro on other machines) 

Some users of VS Preview Builds have run into a problem that despite the extension manager reporting the newest version is installed, an older UI is showing. This is a bug in our extension versioning and you need to completely uninstall Model Builder to resolve. 

To fix... 

1. Uninstall Model Builder from the Extension Manager (in VS: Extensions -> Manage Extensions) and from the VS Installer (in Visual Studio Installer -> Modify Version -> .NET Desktop Development -> ML.NET Model Builder Preview)
2. Ensure Model Builder has been completely removed from this version of VS. It should not show in the extension manager or on right click -> Add Machine Learning. 
3. Reinstall Model Builder in the VS Installer. Update to the latest version from the [marketplace](https://marketplace.visualstudio.com/items?itemName=MLNET.07&ssr=false#overview). 

You should now see an updated UI similar to... 
![image](https://user-images.githubusercontent.com/9122518/113899044-06cc3e00-9792-11eb-85e4-79a6b0d747e6.png)


## Runtime error in code: System.IO.FileNotFoundException: Could not load file or assembly 'Microsoft.ML.Data'. 

Most likely you added Machine Learning to a .NET Full Framework project. The `System.IO.FileNotFoundException: Could not load file or assembly 'Microsoft.ML.Data'` error is caused by a mismatch in Nuget reference styles between your .NET Full Framework project and Model Builder's generated .NET core projects. 

To resolve the problem you will need to make your project compatible with our .NET core projects by using [PackageReference](https://docs.microsoft.com/en-us/nuget/consume-packages/package-references-in-project-files). Here are a few options... 

1. If experimenting with a new project, start again with a new .NET Core project. 
2. If you have a new .NET Framework project it may already be in PackageReference format. PackageReference format will still fail if it has no references added. If you have no packages.config file this is likely your situation. You can get unblocked by... 
- Set the target platform to x64
	`<PlatformTarget>x64</PlatformTarget>`
- Set `<RestoreProjectStyle>PackageReference</RestoreProjectStyle>`. Find more information on this attribute [here](https://docs.microsoft.com/en-us/nuget/consume-packages/package-references-in-project-files#using-packagereference-for-a-project-with-no-packagereferences). 
3. If you have a packages.config file you will need to update to PackageReference. See documentation on how to do that [here](https://docs.microsoft.com/en-us/nuget/consume-packages/migrate-packages-config-to-package-reference).
4. Some projects have limited PackageReference capabilities. If this is the case you may need to update to .NET Core. See this [blog](https://www.hanselman.com/blog/UpgradingAnExistingNETProjectFilesToTheLeanNewCSPROJFormatFromNETCore.aspx) by Scott Hanselman for more help.
