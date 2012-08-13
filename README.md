## Prerequisite
* Java 1.6+
* [Eclipse-SDK-3.7.2](http://download.eclipse.org/eclipse/downloads/drops/R-3.7.2-201202080800/#EclipseSDK)
* [Eclipse DeltaPack-3.7.2](http://download.eclipse.org/eclipse/downloads/drops/R-3.7.2-201202080800/#DeltaPack) (eclipse-3.7.2-delta-pack.zip)

## Prepare Built-In Appspresso SDK

##### 1. [Build Appspresso SDK](http://gitlab.kthcorp.com/appspresso-sdk/master/tree/README.md)

##### 2. Add compressed Appspresso SDK in com.appspresso.cli project

    $ cd {Appspresso SDK folder}/build/output/sdk/
    $ zip -r axhome.zip *
	$ mv axhome.zip {Appspresso Tool folder}/com.appspresso.cli/

	# Result:
	{Appspresso Tool folder}/com.appspresso.cli/
           |..
           |__ axhome.zip

## Export the Appspresso product to multiple platform

##### 1. Set Eclipse Deltapack
Extract eclipse-deltapack-3.7.2.zip to eclipse-deltapack folder in build project
    
    $ unzip eclipse-deltapack-3.7.2.zip
    $ mv eclipse/* {Appspresso Tool folder}/build/eclipse-deltapack

	# Result:
	{Appspresso Tool folder}/build/
           |__ eclipse-deltapack/
                            |__ features/
                            |__ plugins/

##### 2. Run Eclipse-SDK-3.7.2

##### 3. Import Appspresso Tool projects into Workspace
From the main menu bar, select [File > Import..]. The Import wizard opens.
Select [General > Existing Projects into Workspace] and click Next.
Choose "Select root directory" and click the Browse to locate the {Appspresso Tool folder}.
Under Projects select the following project.
Click Finish to start the import.

    build 
    com.appspresso.cli
    com.appspresso.core
    com.appspresso.feature
    com.appspresso.packaging
    com.appspresso.pdk
    com.appspresso.sdk
    com.appspresso.sdk.debug
    com.appspresso.sdk.template

##### 4. Set target platform
open appspresso.target file in com.appspresso.sdk project with Target Editor,
select the Definition tab and click on the "Set as Target Platform" link.

![Appspresso Target](http://appspresso.com/git/appspresso_target.png)

##### 5. Export the product using the Eclipse Product export wizard.
From the main menu bar, select [File > Export..> Plugin-in Development > Eclipse Product]. The following Export wizard page opens.

![Export product1](http://appspresso.com/git/export_product1.png)

The Export for multiple platforms option is only available when PDE detects that the RCP delta pack is installed in the target platform. this option is selected, a second wizard page is available and display a list of available platforms to export.

![Export product2](http://appspresso.com/git/export_product2.png)

Click Finish to start the export.

## Product Export Output

* Appspresso Studio for win32 (_Appspresso1\_1\_2.win32.x86.zip_)
* Appspresso Studio for win64 (_Appspresso1\_1\_2.win32.x86\_64.zip_)
* Appspresso Studio For Mac (_Appspresso1\_1\_2.macosx.cocoa.x86\_64.zip_)
* Metadata repository which can then be used to install using p2 (_repostiory/_)
