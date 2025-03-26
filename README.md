# Image Update Workflow

This repository serves as a prototype for a workflow that enables the automated updating of publicly available images using Renovate. The updated images are then built and pushed into an internal development image registry via a Tekton pipeline that runs at a specified interval. Optionally, the images can also be promoted to an internal production image registry.

## `/images`

Contains all Dockerfiles for the images that are derived from publicly available images. The versions in these Dockerfiles are automatically updated by Renovate.

## `/updates-images`

The update-images pipeline runs at regular intervals and performs the following tasks:
1. Builds images from the Dockerfiles to create internal copies.
2. Pushes the built images to the internal development image registry.
3. Optionally promotes the images to the internal production image registry, if configured.

This workflow ensures that internal images remain up-to-date with publicly available sources while maintaining control over their deployment.