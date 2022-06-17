# Troubleshooting for Model Builder
If troubleshooting does not solve the problem, please file a bug [here](https://github.com/dotnet/machinelearning-modelbuilder/issues/new?template=bug_report.md). 

## Cannot run code from tutorial because PredictedLabel does not exist

In a newer version of ML.NET the property `Prediction` was renamed to `PredictedLabel`. You are referencing an older version of ML.NET. There are a few options for resolving this. 
- Change `PredictedLabel` to `Prediction`.
- Update ML.NET to 1.7.1
- Update Model Builder version to the [latest]([url](https://marketplace.visualstudio.com/items?itemName=MLNET.ModelBuilder2022)) and re-train the model 

## Reset VS 

Sometimes Model Builder doesn't update correctly and VS is still referencing older Model Builder code. If uninstalling and re-installing Model Builder doesn't work, we recommend doing a [clean install of VS](https://docs.microsoft.com/en-us/visualstudio/install/uninstall-visual-studio?view=vs-2019#remove-all-with-installcleanupexe). 

## I cannot "Add Machine Learning" to my project

"Add Machine Learning" isn't an option in the right click menu: 
1. Model Builder can only be added to C# projects. VB is not supported at this time. 
2. Is the extension installed and enabled? You may have disabled the extension at some point due to a performance warning. Check _Extensions -> Manage Extensions -> Installed_. ML.NET Model Builder should be listed and enabled.
3. Is it a UWP Project? There is a known issue - [#1715](https://github.com/dotnet/machinelearning-modelbuilder/issues/1715). Current work around is to create an empty file with extension '.mbconfig'. In VS the file should open in the Model Builder experience. 

I've clicked "Add Machine Learning" and nothing happened or an error happened:
1. The first time "Add Machine Learning" is clicked VS will prompt you to enable the feature (different than the extension being enabled). You can find this setting in _Options -> Environment -> Preview Features -> Enable ML.NET Model Builder._  After the feature is enabled you'll need to click "Add Machine Learning" again. 
2. Are you using a .NET Framework 4.7.2 version project? We have a [bug](https://github.com/dotnet/machinelearning-modelbuilder/issues/1511) for framework projects in Model Builder version 16.6.1.2131904. Update your version or use "Add New Item" window instead. 

## Dev Team Cannot Reproduce (no constant repro on other machines) 

Some users of VS Preview Builds have run into a problem that despite the extension manager reporting the newest version is installed, an older UI is showing. This is a bug in our extension versioning and you need to completely uninstall Model Builder to resolve. 

To fix... 

1. Uninstall (or revert) Model Builder from the Extension Manager (in VS: Extensions -> Manage Extensions) and from the VS Installer (in Visual Studio Installer -> Modify Version -> .NET Desktop Development -> ML.NET Model Builder Preview)
	- If you encounter a problem removing Model Builder from the VS Installer, it can be a sign that your Model Builder extension installation had been corrupted (this happened for a few preview builds in 2020). You may need to uninstall that version of VS.	
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
