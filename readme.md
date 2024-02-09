# Using Syft as SBOM Tool with Different Container Images

Syft is a powerful SBOM (Software Bill of Materials) tool that provides insights into the contents of container images. In this guide, we'll explore how to use Syft with different container images to generate SBOM reports.

## Installation

To install Syft, you can use the following command:

```bash
curl -sSfL https://raw.githubusercontent.com/anchore/syft/main/install.sh | sh
```

Once installed, you can use Syft by executing:

```bash
./bin/syft <image_name>
```

For example:

```bash
./bin/syft alpine
```
![image](https://github.com/wolfi-dev/os/assets/73319030/116531ab-d62b-4ae3-bc39-944e0ad3189f)

## Using Different Image Registries

Syft can also analyze container images from various registries. Here are some examples:

```bash
# Using Syft with an image from chainguard registry
./bin/syft cgr.dev/chainguard/wolfi-base
```
![image](https://github.com/wolfi-dev/os/assets/73319030/990abdee-4efd-4966-83e4-bb1cc68574b6)
```bash
# Using Syft with an image from Google Container Registry (GCR)
./bin/syft gcr.io/distroless/java17-debian12:debug-nonroot
```
![image](https://github.com/wolfi-dev/os/assets/73319030/02db8b88-983f-4f2e-862d-d64956d7da38)

```bash
# Using Syft with an image from Amazon Elastic Container Registry (ECR)
./bin/syft 
```
![image](https://github.com/wolfi-dev/os/assets/73319030/b84b46da-db51-4cd3-a55e-213d0355b5cc)



## My Use Cases for Syft

1. **Dockerfile Not Available**: If the Dockerfile for the image you need to use is not available, Syft can help you understand the contents of the image and its dependencies.

    ```bash
    ./bin/syft <image_name>
    ```

2. **Comparing Images from Different Providers**: Syft can be used to compare packages between two identical images obtained from different providers.

    ```bash
    ./bin/syft <image_provider1/image> > provider1_sbom.txt
    ./bin/syft <image_provider2/image> > provider2_sbom.txt
    diff provider1_sbom.txt provider2_sbom.txt
    ```

3. **Building Images Using Custom Methods**: If you want to create an image using your own methods, Syft can assist in understanding the packages and dependencies needed.

    ```bash
    ./bin/syft redis
    ```
    
