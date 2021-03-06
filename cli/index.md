{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}

# CLI and Dev Tools
{: #cli}

*Last updated: 13 January 2016*

Powerful tools for {{site.data.keyword.Bluemix_short}} and download links.
{:shortdesc}

## ![Command line interfaces](./images/CLI.png) Command line interfaces
{: #downloads}

Download and install command line interfaces to support your {{site.data.keyword.Bluemix_notm}} experience. The Cloud Foundry cf command line interface is a prerequisite for all other {{site.data.keyword.Bluemix_notm}} CLI tools.


| *Cloud Foundry: cf* |	*{{site.data.keyword.Bluemix_notm}}: bx* | 
|---------------------|---------------|
| [Download CLI](https://github.com/cloudfoundry/cli/releases){: new_window}  <br> [View Docs](./reference/cfcommands/index.html) | [Download CLI](http://clis.{DomainName}/){: new_window} <br> [View Docs](./reference/bluemix_cli/index.html)| 

| *{{site.data.keyword.Bluemix_notm}} Live Sync: bl* |
|---------------|---------------|
| [Mac Installer](ftp://public.dhe.ibm.com/cloud/bluemix/cli/Bluemix_bl.pkg){: new_window} <br> [Windows Installer](ftp://public.dhe.ibm.com/cloud/bluemix/cli/Bluemix_bl.exe){: new_window} <br> [View Docs](./reference/bl/index.html) |


## ![Command line interface plug-ins](./images/CLI_Plugin.png) Command line interface plug-ins

Easily extend your {{site.data.keyword.Bluemix_notm}} command line interface with more commands. To access the {{site.data.keyword.Bluemix_notm}} command line interface plug-ins, see the [{{site.data.keyword.Bluemix_notm}} CLI Plug-in Repository](http://plugins.{DomainName}/){: new_window}.

1. To install cf CLI plug-ins from the {{site.data.keyword.Bluemix_notm}} registry, set the plug-in registry endpoint:
```
cf add-plugin-repo bluemix-cf-staging http://plugins.ng.bluemix.net
```
2. Run the following command to install a plug-in:
```
cf install-plugin plugin_name -r bluemix-cf-staging
```

| *Active Deploy* | *Admin Console* | *Development Mode* | 
|-----------------|-----------------|-----------------|
| Plug-in name: active-deploy <br>  [View Docs](../services/ActiveDeploy/index.html#cli) |  Plug-in name: bluemix-admin <br> [View Docs](../cli/plugins/bluemix_admin/index.html) | Plug-in name: development-name <br> [View Docs](./plugins/dev_mode/index.html) | 

### Extend your {{site.data.keyword.Bluemix_notm}} command line interface: bx
1. To install {{site.data.keyword.Bluemix_notm}} CLI plug-ins from the {{site.data.keyword.Bluemix_notm}} registry, set the plug-in registry endpoint:
```
bluemix plugin repo-add bluemix-bx-staging http://plugins.ng.bluemix.net
```
2. Run the following command to install a plug-in:
```
bluemix plugin install plugin_name -r bluemix-bx-staging
```

| *{{site.data.keyword.IBM}} Containers for {{site.data.keyword.Bluemix_notm}}* | *VPN* |
|-----|-----|
| Plug-in name: ibm-containers <br> [View Docs](https://www.{DomainName}/docs/containers/container_cli_ov.html#container_cli_cfic_install) | Plug-in name: VPN <br> [View Docs](./plugins/vpn/index.html) |

## ![Integrated development tools](./images/Integrated_Dev_Tools.png) Integrated development tools


Download and install plug-ins to integrate your favorite {{site.data.keyword.Bluemix_notm}} services.

| *{{site.data.keyword.jazzhub_short}}* | *Liberty for Java* | *MobileFirst* | *{{site.data.keyword.rules_short}}* |
|-------------|----------|----------|----------|
| [Egit Eclipse Plug-in](https://hub.jazz.net/docs/reference/gitclient/#eclipse_using_egit){: new_window} <br> [RTC Eclipse Plug-in](https://hub.jazz.net/docs/reference/gitclient/#eclipse_using_rtc){: new_window} | [Liberty Eclipse Plug-in](https://developer.ibm.com/wasdev/downloads/liberty-profile-using-eclipse/){: new_window} | [Eclipse Plug-in](https://marketplace.eclipse.org/content/ibm-mobilefirst-platform-studio){: new_window} | [Rules Designer Eclipse Plug-in](../services/rules/index.html#rulov002) |
