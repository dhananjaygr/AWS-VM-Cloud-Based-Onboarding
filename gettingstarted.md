---
sidebar_position: 43
slug: /Admin/LabDeveloper/Guide For Onboarding Labs/VM + Cloud Based Labs Onboarding/AWS VM + Cloud Based Onboarding.md
---

# AWS VM + Cloud Based Onboarding
 
## Overview:
 
This document provides a comprehensive guide to the end-to-end process of onboarding a VM + AWS based lab scenario using the CloudLabs Admin Portal. For instance, if you need the users to create resources in AWS by following a certain lab guide or document and want a pre-deploy VM in which the users will perform the tasks, then this is the scenario you want to proceed with. Follow the steps outlined below for a successful lab setup.

In this document you will be going through with the below topics:

  - [Prerequisites](#prerequisites)
  
  - [Information to utilize for VM with AWS based lab onboarding](#information-to-utilize-for-vm-with-aws-based-lab-onboarding)

  - [Setup Template in CloudLabs for AWS](#setup-template-in-cloudlabs-for-aws)

  - [Use VM Images in CloudFormation template](#use-vm-images-in-cloudformation-template)

  - [Setup On Demand Lab on CloudLabs Admin Portal](#setup-on-demand-lab-on-cloudlabs-admin-portal)

  - [Activate the lab](#activate-the-lab)

  - [Common Issues and Resolutions](#common-issues-and-resolutions) 
  
## Prerequisites

Before you begin onboarding a VM + AWS based lab through CloudLabs, ensure you have the following prerequisites:

1. Admin access to [CloudLabs Admin Centre](https://admin.cloudlabs.ai/) (If access is unavailable, kindly reach out to your point of contact or [CloudLabs Support](../../GuideForOnboardingLabs/ContactSupport.md)).

2. An active subscription in CloudLabs Admin Portal. Refer [How to Onboard AWS Accounts to CloudLabs Portal](https://docs.cloudlabs.ai/LabDeveloper/OnboardingAWSAccountstoCloudLabs) document.

3. Lab Guide/Reference documents containing necessary instructions, often provided through GitHub which are in GitMarkdown format.


## Information to utilize for VM with AWS based lab onboarding

To onboard a VM + AWS based lab to CloudLabs, use the below details:

- **Subscription Types**:  To onboard a VM + AWS based lab, you should firstly determine what type of access the participants would require and post that you need to select the Subscription type from one of the three types below that CloudLabs offers. It is highly recommended that you apply access and policy constraints for the chosen subscription type.
   
    - **Dedicated Subscription** : One of the AWS Organization Member account will be given to the one user.

    - **Dedicated Tenant**: When a access to the Organization root account is needed. 
  

Once you are ready to Onboard the labs on CloudLabs Admin Portal, you need to follow the instructions mentioned below:

*Let’s begin with the Onboarding Process*:

## Setup Template in CloudLabs for AWS

1. The first step in the onboarding process is to add a template in CloudLabs Admin Portal. 

2. You can follow the detailed guide mentioned here to login to the CloudLabs Admin Portal

   - **[Access CloudLabs Admin Portal](../../../OnboardingDocs/AccessCloudLabsAdminCenter.md)**

3. Follow the below mentioned guide to Add Template in CloudLabs.

   - **[Add AWS template for VM + Cloud Based Lab](https://dev-cl-docs.azurewebsites.net/Admin/LabDeveloper/Guide%20For%20Onboarding%20Labs/VM%20Based%20Labs%20Onboarding/AWS%20VM%20Based%20Lab%20Onboarding/Adding%20Template%20For%20VM%20Based%20Lab)**

You have successfully onboarded the template into CloudLabs.

## Use VM Images in CloudFormation template

In AWS, there are two ways that you can use Amazon Machine Images (AMIs) to deploy a virtual machine. You can either utilize AWS Marketplace AMIs or create custom AMIs through AWS's EC2 Image Builder or other methods.

### Amazon Machine Images (AMIs) 

1. To deploy a virtual machine using any Amazon Machine Image (AMI) in AWS, you need to specify the AMI ID for the instance in the resources section of your CloudFormation template. You can find the AMI ID details from the AWS Management Console or using AWS CLI commands.

```
{
  "Resources": {
    "MyEC2Instance": {
      "Type": "AWS::EC2::Instance",
      "Properties": {
        "ImageId": "<AMI ID>",  
        "InstanceType": "<Instance type>", 
        "KeyName": "<KeyPair>",     
        "SecurityGroupIds": [
          "<security group(s)>"            
        ],
        "Tags": [
          {
            "Key": "Name",
            "Value": "<Name tag for the instance>"  
          }
        ]
      }
    }
  }
}
```
### Amazon EBS

1. You can follow the detailed guide mentioned below on how to use AWS Amazon EBS service to create a custom Amazon Machine Image (AMI) and utilize it.

   - **[Creating the Custom AMI](https://docs.cloudlabs.ai/Admin/LabDeveloper/Guide%20For%20Onboarding%20Labs/VM%20Based%20Labs%20Onboarding/AWS%20VM%20Based%20Lab%20Onboarding/Custom%20AMI)**

2. You can create custom Amazon Machine Images (AMIs) for both Windows and Linux instances based on the lab requirements. The below mentioned guide will navigate you to the AWS CloudFormation section of Adding Template in CloudLabs.
  
   - **[Add template in CloudLabs - AWS CloudFormation template](https://docs.cloudlabs.ai/LabDeveloper/AddingAWSTemplate/)**

## Setup On Demand Lab on CloudLabs Admin Portal

1. You'll need to create the On-Demand Lab (ODL) and map the template you've created in the previous step. The creation of ODL is only for Admins and not users.

    > **Note:** One template can be mapped with multiple ODLs.
    
2. The onboarding process can vary depending on the requirements of your lab scenario.

3. To create ODL from CloudLabs Admin Portal follow instructions mentioned in the below guide: 

    - **[Create On Demand Lab in CloudLabs Admin Portal](https://docs.cloudlabs.ai/LabDeveloper/CreatingODL)**

You have successfully onboarded the On-Demand Lab (ODL) on CloudLabs Admin Portal.

## Activate the lab

1. From the **On Demand Labs** Page _(1)_, choose your ODL _(2)_ and click on the Users icon _(3)_ to register into the environment. 

   ![](/img/OnboardingDocs/ondemandlab.png)

2. Click on **+ Add User** and enter your details then click on **Submit**. 

   ![](/img/OnboardingDocs/adduser-v2.png)

3. Now you have successfully registered yourself as a user. 

4. Within the **Users** page, you will find an instance registered under your name, indicated by its status being in the Approved state _(1)_. Proceed by clicking the **Launch** _(2)_ button.

   ![](/img/OnboardingDocs/odl-approved1.png)

5. Now you will be navigated to a different browser tab where you will be able to view the page as shown in the screenshot below. On this page, click on the **Launch Lab** button.

   ![](/img/OnboardingDocs/launchlab.png)

6. Upon clicking the **Launch Lab** button, the deployment process will initiate, leading you to the screen illustrated in the provided screenshot below:

   ![](/img/OnboardingDocs/odl-lablaunch.png)

7. After the instance is successfully deployed, you will encounter the screen depicted in the provided screenshot:  

   ![](/img/OnboardingDocs/labvm1.png)

8. You can also activate the lab at bulk using Bit.ly URL by following the below steps.

9. From the **On Demand Labs** Page, choose your ODL _(1)_ and click on the Elipses icon _(2)_ and select **Activate Codes** to create an activation code. 

   ![](/img/OnboardingDocs/odl-select-odl.png)


10. Click on **+ ADD ACTIVATION CODE** 

    ![](/img/OnboardingDocs/odl-add-activation-code.png)

11. Provide the below values for the Activation Code properties.

    - **Name:** The Activation code should always follow the naming convention **ACTIVATE<**-**ODL-ID**-**>**. For instance, if your ODL ID is 1462, then the Activation Code will be **ACTIVATE1462**.

    - **Customer:** Provide your company or customer name.

    - **City:** Provide your city name.

    - **Country:** Select your country from the dropdown.

    - **Expiry Date:** Select an expiry date for the Activation code, post which the Activation code will be invalid.

    Finally, click **Submit** to save details.

    ![](/img/OnboardingDocs/odl-provide-activation-code-details.png)

12. Copy the Bit.ly URL and share it with the users.

    ![](/img/OnboardingDocs/odl-copy-bitly-url.png)

13. Users can activate their labs by following the below steps:
     -	Navigate to the Bit.ly URL.
     -	Provide the required details.
     -	Click on Submit.

     ![](/img/OnboardingDocs/register.png)

14. To find more information on ODL and Manging the lab click on the below link to access the guide. You can find information on how to invite users, manage users, extend lab duration and much more.

    [Manage Access](https://docs.cloudlabs.ai/Instructor/ManageLabs/)

## Common Issues and Resolutions 

1. The CloudFormation Template & Parameter files must be stored in the S3 Storage Bucket. The storage bucket and the objects must be publicly accessible, steps to make a bucket public are described here [Creating a Bucket with Public Access](https://spektra-bucket.s3.us-west-2.amazonaws.com/publics3bucket.docx) once the files are uploaded you can retrieve the URL & provide it in the CloudFormation details tab in the CloudLabs Template.

2. Make sure that **Enable EC2 Access Over Http** flag is enabled in CloudLabs Template, and **ACI deployment style** should be given as **Default** in On Demand Lab settings.
For more information on how to enable RDP/SSH access for **EC2** refer following documentation: [How to Enable RDP/SSH Access over HTTPS for EC2](https://docs.cloudlabs.ai/LabDeveloper/EC2OverHttps) 

3. CloudFormation templates and parameters files syntax must be correct. refer to below sample Cloudformation template and parameter files urls:

   * **Cloudformation Template File**: [sample Cloudformation template file](https://spektra-cft-templates.s3.amazonaws.com/cloudlabsdemo.json)

   * **Parameters File**:   [sample parameters file](https://spektra-cft-templates.s3.amazonaws.com/cloudlabsdemo.parameters.json) 





