# node-docker-xslt-processor
Process XLST transform with docker and node using this repo's java code: https://github.com/cambridge-collection/cudl-data-processing-xslt?tab=readme-ov-file

## Dependencies

1. [Docker](https://www.docker.com/products/docker-desktop/)
2. [Node](https://nodejs.org/en/download)

## How it works

![Untitled Diagram drawio](https://github.com/shenuka-jayasinghe/node-docker-xslt-processor/assets/137282472/81a7688f-151f-40d3-8b54-b7290098efd8)


The async function, ```processDataWithDocker(teiDirectory, isSudoDocker)``` takes a TEI directory (:string) as an argument. It then initiates a Docker container through a volume mount to the location where our JS function is executed. The container processes the TEI XML using XSLT and converts it into JSON. The resulting JSON is then outputted to the working directory, after which the Docker container is closed.

### Steps

1. In line 61 of `teiToJSON.js`, provide the TEI directory to be processed as the first argument.
   
2. If your DockerHub credentials require `sudo` for pulling images from online repositories, set the second argument to `true`. Otherwise, set it to `false`.

### Example

```js
processDataWithDocker('/home/linux/Documents/github/dl-data-samples/source-data/data/items/data/tei/MS-TEST-ITEM-00002/', true)

