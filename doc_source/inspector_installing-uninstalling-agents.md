# Installing Amazon Inspector Agents<a name="inspector_installing-uninstalling-agents"></a>

The Amazon Inspector Agent can be installed using the Systems Manager Run Command on multiple instances \(including both Linux\-based and Windows\-based instances\), or individually by signing in to each EC2 instance\. The procedures below provide instructions for both methods\.


+ [To install the Amazon Inspector Agent on multiple EC2 instances using the Systems Manager Run Command](#install-run-command)
+ [To install the Amazon Inspector Agent on a Linux\-based EC2 instance](#install-linux)
+ [To install the Amazon Inspector Agent on a Windows\-based EC2 instance](#install-windows)

**Note**  
The following procedures are functional in all regions that are supported by Amazon Inspector\.

## To install the Amazon Inspector Agent on multiple EC2 instances using the Systems Manager Run Command<a name="install-run-command"></a>

You can install the Amazon Inspector Agent on your EC2 instances using the [Systems Manager Run Command](http://docs.aws.amazon.com/systems-manager/latest/userguide/execute-remote-commands.html)\. This enables you to install the agent remotely and on multiple instances \(both Linux\-based and Windows\-based instances with the same command\) at once\. 

**Important**  
To utilize this option, make sure that your EC2 instance has the SSM Agent installed and has an IAM role that allows Run Command\. The SSM Agent is installed, by default, on Amazon EC2 Windows instances and Amazon Linux instances\. Amazon EC2 Systems Manager requires an IAM role for EC2 instances that will process commands and a separate role for users executing commands\. For more information, see [Installing and Configuring SSM Agent](http://docs.aws.amazon.com/systems-manager/latest/userguide/ssm-agent.html)and [Configuring Security Roles for System Manager](http://docs.aws.amazon.com/systems-manager/latest/userguide/systems-manager-access.html)\. 

1. Open the Amazon EC2 console at [https://console\.aws\.amazon\.com/ec2/](https://console.aws.amazon.com/ec2/)\. 

1. In the navigation pane under **Systems Manager Services**, choose **Run Command**\. 

1. Choose **Run a command**\. 

1. For **Command document**, choose the document named 

   **AmazonInspector\-ManageAWSAgent** owned by **Amazon**\. This document contains the script for installing the Amazon Inspector Agent on EC2 instances\.

1. Specify your EC2 instances either by choosing the **Specifying a Tag** option or by **Manually Selecting Instances** and then selecting **Select instances**\. To install the agent on all the instances in the assessment target, you can specify the same tags used for creating the assessment target\. 

1. Provide your choices for the rest of the available options using the instructions in [Executing Commands from the EC2 Console](http://docs.aws.amazon.com/systems-manager/latest/userguide/rc-console.html), and then select **Run**\.

## To install the Amazon Inspector Agent on a Linux\-based EC2 instance<a name="install-linux"></a>

1. Sign in to your EC2 instance running a Linux\-based operating system where you want to install the Amazon Inspector Agent\.
**Note**  
For more information about operating systems supported for Amazon Inspector see [Amazon Inspector Supported Operating Systems and Regions](inspector_supported_os_regions.md)\.

1. Download the agent installation script by running either of the following commands:

   + wget https://d1wk0tztpsntt1\.cloudfront\.net/linux/latest/install

   + curl \-O https://d1wk0tztpsntt1\.cloudfront\.net/linux/latest/install

1. \(Optional\) Verify that the Amazon Inspector Agent installation script is not altered or corrupted\. For more information, see [\(Optional\) Verify the Signature of the Amazon Inspector Agent Installation Script on Linux\-based Operating Systems](inspector_verify-sig-agent-download-linux.md)\.

1. To install the agent, run sudo bash install\.
**Note**  
As updates for the Amazon Inspector Agent become available, they are automatically downloaded from Amazon S3 and applied\. For more information, see [Amazon Inspector Agent Updates](inspector_agents.md#agent-updates)\.  
If you want to skip this auto\-update process, make sure to run the following command when you install the agent:  
sudo bash install \-u false
**Note**  
\(Optional\) To remove the agent installation script, run rm install \.

1. Verify that the following files required for the agent to be successfully installed and functioning properly are installed:

   + libcurl3

   + libgcc1

   + libc6

   + libstdc\+\+6

   + libssl1\.0\.1

   + libpcap0\.8

## To install the Amazon Inspector Agent on a Windows\-based EC2 instance<a name="install-windows"></a>

1. Sign in to your EC2 instance running a Windows\-based operating system where you want to install the Amazon Inspector Agent\.
**Note**  
For more information about operating systems supported for Amazon Inspector see [Amazon Inspector Supported Operating Systems and Regions](inspector_supported_os_regions.md)\.

1. Download the following \.exe file: https://d1wk0tztpsntt1\.cloudfront\.net/windows/installer/latest/AWSAgentInstall\.exe

1. Open a command prompt window \(with Administrative permissions\), navigate to the location where you saved the downloaded AWSAgentInstall\.exe, and run AWSAgentInstall\.exe to install the Amazon Inspector Agent\.
**Note**  
As updates for the Amazon Inspector Agent become available, they are automatically downloaded from Amazon S3 and applied\. For more information, see [Amazon Inspector Agent Updates](inspector_agents.md#agent-updates)\.  
If you want to skip this auto\-update process, make sure to run this command to install the Amazon Inspector Agent\.  
AWSAgentInstall\.exe AUTOUPDATE=No