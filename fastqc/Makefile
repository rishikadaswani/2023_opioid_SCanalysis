DOCKERHUB_USERNAME=rishikadaswani
IMAGE_VERSION=v0.1
IMAGE_NAME=snrnaseq

# Docker 	
build:
	docker build -t $(DOCKERHUB_USERNAME)/$(IMAGE_NAME):$(IMAGE_VERSION) .

run:
	docker run -it -v /Users/rishikadaswani/Desktop/2023_opioid_SCanalysis:/home $(DOCKERHUB_USERNAME)/$(IMAGE_NAME):$(IMAGE_VERSION)

push:
	docker push $(DOCKERHUB_USERNAME)/$(IMAGE_NAME):$(IMAGE_VERSION)

fastqc:
	mkdir -p fastqc_results
	fastqc -o fastqc_results ../data/GEX-R3-AS-12162022_S1_L001_R1_001.fastq.gz ../data/GEX-R3-AS-12162022_S1_L001_R2_001.fastq.gz
	
sockeye_pull:
	module load singularity; \
	singularity pull --name scrnaseq docker://$(DOCKERHUB_USERNAME)/$(IMAGE_NAME):$(IMAGE_VERSION)

sockeye_fastqc:
	sh fastqc.sh /project/st-singha53-1/datasets/fentanyl/scrnaseq

qstat:
	qstat -u $(USER)
