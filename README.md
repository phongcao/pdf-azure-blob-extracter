# pdf-azure-blob-extracter

This notebook reads a PDF file, extracts its images and content and upload them to
Azure Blob storage.

After running, you can find the following blobs on Azure Blob storage:

```
[Container]/[PDF file name without ext]/content.md
[Container]/[PDF file name without ext]/img_1.png
[Container]/[PDF file name without ext]/img_2.png
[Container]/[PDF file name without ext]/img_3.png
...
```

In the content.md file, the embedded images are extracted and replaced by file names:

```
Text 1

![img_1.png](img_1.png)


Text 2

![img_2.png](img_2.png)


Text 3

![img_3.png](img_3.png)
```

It's easy to manipulate those image links to inject
[SAS tokens](https://learn.microsoft.com/en-us/azure/storage/common/storage-sas-overview)
so that they can be fully rendered.

## How to run

1. Copy the `.env.template` file to `.env` and fill in the required info.
2. Upgrade pip: `pip install --upgrade pip`.
3. Install dependencies: `pip install -r requirements.txt`.
4. Modify the input file name, default is `userguide.pdf`.
5. Modify the output file name, default is `userguide.md`.
6. Modify footer and header font size under `Special setttings` if needed.
7. Run the notebook and check the blob storage for the extracted images and content.
