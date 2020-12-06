CC=g++
CPP_VERSION=c++11

GASAL_PATH=../GASAL2/include
LIBSTATGEN_PATH=../libStatGen/

OBJ_GASAL_PATH=../GASAL2/obj/

GASAL_OBJS = $(wildcard $(OBJ_GASAL_PATH)*.c*)

OBJ_LSG_BAM_PATH=../libStatGen/bam/obj/
OBJ_LSG_GENERAL_PATH=../libStatGen/general/obj/
OBJ_LSG_VCF_PATH=../libStatGen/vcf/obj/
OBJ_LSG_FASTQ_PATH=../libStatGen/fastq/obj/
OBJ_LSG_GLF_PATH=../libStatGen/glf/obj/
OBJ_LSG_SAMTOOLS_PATH=../libStatGen/samtools/obj/
OBJ_ZLIB_PATH=../zlib-1.2.11/

BAM_OBJS = $(wildcard $(OBJ_LSG_BAM_PATH)*.o)
GENERAL_OBJS = $(wildcard $(OBJ_LSG_GENERAL_PATH)*.o)
VCF_OBJS = $(wildcard $(OBJ_LSG_VCF_PATH)*.o)
FASTQ_OBJS = $(wildcard $(OBJ_LSG_FASTQ_PATH)*.o)
GLF_OBJS = $(wildcard $(OBJ_LSG_GLF_PATH)*.o)
SAMTOOLS_OBJS = $(wildcard $(OBJ_LSG_SAMTOOLS_PATH)*.o)
ZLIB_OBJS = $(wildcard $(OBJ_ZLIB_PATH)*.o)

all: $(BAM_OBJS) $(GENERAL_OBJS) $(VCF_OBJS) $(FASTQ_OBJS) $(GLF_OBJS) $(SAMTOOLS_OBJS)
	$(CC) -std=$(CPP_VERSION) -I $(GASAL_PATH) -I $(LIBSTATGEN_PATH)include -I $(OBJ_ZLIB_PATH) -L /opt/area/shared/programs/x86_64/cuda/11.0.3_450.51.06/lib64 -lcudart -fopenmp main.cpp -o main $(GASAL_OBJS) $(BAM_OBJS) $(GENERAL_OBJS) $(VCF_OBJS) $(FASTQ_OBJS) $(GLF_OBJS) $(ZLIB_OBJS) $(SAMTOOLS_OBJS)

clean:
	rm -rf *o main
	rm -rf prova.*
run:
	./main -y local -p -t ./query_batch.fasta ./target_batch.fasta > prova.txt
