# gatk4-cnn-variant-filter

### Purpose :

This workflow takes an input CRAM to call variants with HaplotypeCaller
then filters the calls with the CNNVariant neural net tool.
The site-level scores are added to the INFO field of the VCF. The architecture arguments, 
info_key and tensor type arguments MUST be in agreement (e.g. 2D models must have 
tensor_type of read_tensor and info_key CNN_2D, 1D models have tensor_type 
reference and info_key CNN_1D). The INFO field key will be "1D_CNN" or "2D_CNN" 
depending on the neural net architecture used for inference. The architecture arguments 
specify pre-trained networks. New networks can be trained by the 
GATK tools: CNNVariantWriteTensors and CNNVariantTrain. The CRAM could be generated 
by the [single-sample pipeline] (https://github.com/gatk-workflows/gatk4-data-processing/blob/master/processing-for-variant-discovery-gatk4.wdl)
Also accepts a BAM as the input file in which case a BAM index is required as well.

### Requirements/expectations :
 - CRAM/BAM
 - BAM Index (if input is BAM) 

### Output :
 - Filtered VCF 
 - Filtered VCF index. 

### Important Note :
- Runtime parameters are optimized for Broad's Google Cloud Platform implementation. 
- For help running workflows on the Google Cloud Platform or locally please
view the following tutorial [(How to) Execute Workflows from the gatk-workflows Git Organization](https://software.broadinstitute.org/gatk/documentation/article?id=12521).
- Please post questions to the [GATK forum](https://gatkforums.broadinstitute.org/gatk/categories/ask-the-team).
- Please visit the [User Guide](https://software.broadinstitute.org/gatk/documentation/) site for more documentation on our workflows and tools. 

### LICENSING :
 This script is released under the WDL source code license (BSD-3) (see LICENSE in
 https://github.com/broadinstitute/wdl). Note however that the programs it calls may
 be subject to different licenses. Users are responsible for checking that they are
 authorized to run all programs before running this script. Please see the docker
 page at https://hub.docker.com/r/broadinstitute/genomes-in-the-cloud/ for detailed
 licensing information pertaining to the included programs. 
