# Docker image for dc5 - Emulating Global Ocean

---
## Build

Start the build

- Set the tag (do not use `latest` or `stable`)
```bash
export IMAGE_TAG=0.0.1
```
- Build the image
```bash
docker build \
  --progress=plain \
  --no-cache \
  -f docker/Dockerfile \
  -t ghcr.io/ocean-ai-data-challenges/dc5-marine-biodiversity-prediction:$IMAGE_TAG \
  .
```

---
## Test the image

- Start a container:
    - In console mode
```bash
docker run -it --rm --name dc5 ghcr.io/ocean-ai-data-challenges/dc5-marine-biodiversity-prediction:$IMAGE_TAG bash
```
    - In graphical mode (jupyterlab)
```bash
docker run --rm -p 8888:8888 --name dc5-lab ghcr.io/ocean-ai-data-challenges/dc5-marine-biodiversity-prediction:$IMAGE_TAG
```
- Test
```bash
python -c "import dc5"
```
- If needed, remove the container
    - In console mode
```bash
docker rm --force dc5
```
    - In graphical mode (jupyterlab)
```bash
docker rm --force dc5-lab
```

---
## Publish the image to the Github registry

```bash
docker push ghcr.io/ocean-ai-data-challenges/dc5-marine-biodiversity-prediction:$IMAGE_TAG
```

---
## Set the `latest` and `stable` versions

- stable
```bash
# Define TAG used for stable
export TAG_FOR_STABLE=0.0.1

# Pull image
docker pull ghcr.io/ocean-ai-data-challenges/dc5-marine-biodiversity-prediction:$TAG_FOR_STABLE
# Tag it as stable
docker tag ghcr.io/ocean-ai-data-challenges/dc5-marine-biodiversity-prediction:$TAG_FOR_STABLE ghcr.io/ocean-ai-data-challenges/dc5-marine-biodiversity-prediction:stable
# And push it
docker push ghcr.io/ocean-ai-data-challenges/dc5-marine-biodiversity-prediction:stable
```
- latest
```bash
# Define TAG used for latest 
export TAG_FOR_LATEST=0.0.1

# Pull image
docker pull ghcr.io/ocean-ai-data-challenges/dc5-marine-biodiversity-prediction:$TAG_FOR_LATEST
# Tag it as latest
docker tag ghcr.io/ocean-ai-data-challenges/dc5-marine-biodiversity-prediction:$TAG_FOR_LATEST ghcr.io/ocean-ai-data-challenges/dc5-marine-biodiversity-prediction:latest
# And push it
docker push ghcr.io/ocean-ai-data-challenges/dc5-marine-biodiversity-prediction:latest
```
