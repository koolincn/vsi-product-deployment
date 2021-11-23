# vsi-product-deployment
This is a sample of the vsi product deployment in the VPC environment. 
# Prerequisites

1. Create an IBM Cloud Object Storage bucket and upload the qcow2 image, which will be used to create a custom image in your account. For more information, see the following links:
   * [Getting started with Cloud Object Storage](https://cloud.ibm.com/docs/cloud-object-storage?topic=cloud-object-storage-getting-started-cloud-object-storage)
   * [Images](https://cloud.ibm.com/docs/vpc?topic=vpc-about-images)
2. Create a Virtual Private Cloud (VPC) and subnet. For more information, see [Getting started with VPC](https://cloud.ibm.com/docs/vpc?topic=vpc-getting-started).
3. Create a [SSH key](https://cloud.ibm.com/docs/vpc?topic=vpc-ssh-keys).
4. Create a [virtual server instance](https://cloud.ibm.com/docs/vpc?topic=vpc-creating-virtual-servers).

# Import your custom image to all supported regions
When you are ready to make your image publicly available, import it to every region in which you want your solution to be available. 

# Create your Terraform template

Before you begin, make sure that you have the following IBM Cloud Identity and Access Management (IAM) permissions:

 * Manager service access role for IBM Cloud Schematics
 * Operator platform role for VPC Infrastructure

For more details, see [Creating Terraform templates](https://cloud.ibm.com/docs/schematics?topic=schematics-create-tf-config).  

# Onboard your Terraform template to the IBM Cloud catalog

The onboarding process includes importing your `.tgz` file that you created in the previous section to a private catalog, configuring the deployment values, and then validating the Terraform template. For more details, see [Onboarding a virtual server image](https://cloud.ibm.com/docs/third-party?topic=third-party-vsimage-onboard).

# Update the visibility of your image (patch API)

You can make your virtual server image public only after you validate your Terraform template, and IBM Cloud has granted you access to the REST API you use to update the image visibility. If you run into issues, you can contact us by going **Partner Center** > **My products** > **Help icon**. 

# Publishing a new version

To publish a new version of your image, complete the following steps: 

1. Import the new version as described in the previous Import your custom image to all supported regions section.
2. Edit the `variables.tf` file by updating the image_name variable. 
3. Create an updated GitHub release to create a new `.tgz` file, and note the new URL as previously described in the Create GIT release for artifacts and .tgz section.
4. Onboard the new version in your private catalog as previously described in the Onboard your Terraform template section. 
5. Make your image public as previously described. 
