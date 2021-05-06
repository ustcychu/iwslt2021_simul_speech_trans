# USTC-NELSLIP Simultaneous Translation systems on IWSLT 2021 
## En-De Text-to-Text Translation

This section introduces the usage of En-De Text-to-Text Translation , including segmentation and unsegmentation ways. Note the latter setting also runs on `IWSLT-tst2018` test set, by concating sentences in a document to a long sentence, we generate 14 long sentences in total. So we will provide results on both `tst-common` and `IWSLT tst2018` test sets.

### Usage 
The docker image runs with outside directory 
The following is the template command for all configurations below.

```shell
docker run --rm -it -v $ROOT_DIR/modelfile/:/root/modelfile/ \
                    -v $ROOT_DIR/scripts/:/root/scripts/ \
                    reg.deeplearning.cn/ayers/superbrain-pytorch:1.7-cuda10.2-cudnn7-devel-ubuntu16.04-final \
                    bash /root/scripts/scripts_mt/$config_shell $sourcefile $targetfile $outputdir
```

where `$ROOT_DIR` is the absolute path of our submission package unzipped, `$config_shell` is the shell to shell for each configuration to be run, `$sourcefile` is the input file to be translated,  `$targetfile` is the reference file ,which will be used for calculate BLEU and AL,  `$outputdir` is the output directory for restore `intance.log` and results scores.

### Config and Results

This part provide short introduction for `$config_shell`, then give the results on MUSTC-v2 tst-common test set for segmentation and unsegmentation, and the results on IWSLT tst2018 test sets.

- **Low-config-1:** 
  1. Segmentation: `$config_shell=12-ende-t2t-seg-low-ens.sh`
  2. Unegmentation: `$config_shell=22-ende-t2t-unseg-low-ens.sh`
- **Mid-config-1:** 
  1. Segmentation: `$config_shell=14-ende-t2t-seg-mid-ens.sh`
  2. Unegmentation: `$config_shell=24-ende-t2t-unseg-mid-ens.sh`
- **High-config-1:**
  1. Segmentation: `$config_shell=16-ende-t2t-seg-high-ens.sh`
  2. Unegmentation: `$config_shell=26-ende-t2t-unseg-high-ens.sh`

The folowing table presents the results on `MUSTCv2-tst-common` test set by segmentation way:

|Configuration|BLEU|AL|AP|DAL|
| ---- | ---- | ---- | ---- | ---- |
|Low-config-1|33.12|2.69|0.64|4.45|
|Mid-config-1|34.85|5.88|0.80|9.02|
|High-config-1|35.60|12.41|0.95|15.43|


The folowing table presents the results on `IWSLT-tst-2018` test set by unsegmentation way:

|Configuration|BLEU|AL|AP|DAL|
| ---- | ---- | ---- | ---- | ---- |
|Low-config-1|34.66|2.39|0.50|21.71|
|Mid-config-1|36.56|2.53|0.50|30.67|
|High-config-1|36.81|3.19|0.50|32.92|




## En-Ja Text-to-Text Translation
This section introduces the usage of En-Ja Text-to-Text Translation , including segmentation and unsegmentation ways. 

### Usage 

Please refer to Usage in En-De Text-to-Text Translation.



### Config and Results

This part provide short introduction for `$config_shell`, then give the results on `IWSLT-teddev2021` dev set for segmentation and unsegmentation.

- **Low-config-1:** 
  1. Segmentation: `$config_shell=32-enja-t2t-seg-low-ens1.sh`
  2. Unegmentation: `$config_shell=42-enja-t2t-unseg-low-ens1.sh`
- **Low-config-2:** 
  1. Segmentation: `$config_shell=33-enja-t2t-seg-low-ens2.sh`
  2. Unegmentation: `$config_shell=43-enja-t2t-unseg-low-ens2.sh`
- **Mid-config-1:** 
  1. Segmentation: `$config_shell=34-enja-t2t-seg-mid-sig1.sh`
  2. Unegmentation: `$config_shell=44-enja-t2t-unseg-mid-sig1.sh`
- **Mid-config-2:** 
  1. Segmentation: `$config_shell=35-enja-t2t-seg-mid-sig2.sh`
  2. Unegmentation: `$config_shell=45-enja-t2t-unseg-mid-sig2.sh`
- **High-config-1:** 
  1. Segmentation: `$config_shell=36-enja-t2t-seg-high-sig.sh`
  2. Unegmentation: `$config_shell=46-enja-t2t-unseg-high-sig.sh`


The folowing table presents the results on `IWSLT-teddev2021` dev set by segmentation way:
|Configuration|BLEU|AL|AP|DAL|
| ---- | ---- | ---- | ---- | ---- |
|Low-config-1|15.18|3.50|0.74|6.09|
|Low-config-2|15.53|4.50|0.78|7.38|
|Mid-config-1|16.61|6.75|0.89|9.62|
|Mid-config-2|16.68|7.86|0.92|10.41|
|High-config-1|16.83|10.88|0.97|12.74|

## En-De Speech-to-Text Translation 

In this section, three systems are provided to help solve the Speech-to-Text Translation Task, including (1)End to End single model ; (2) End to End model ensemble;(3) Pipeline model ensemble. The first two systems will provide results on all latency regimes ( low, medium and high) and the Pipeline model ensemble system only provide results on medium and high latency regimes.  All these three models are tested on `tst-common` by segmentation way and `IWSLT tst2018` test sets by unsegmentation way. 

### System 1:  End-to-End single model

The following is the template command for all configurations in system 1.

```shell
docker run --rm -it -v $ROOT_DIR/modelfile/:/root/modelfile/ \
                    -v $ROOT_DIR/scripts/:/root/scripts/ \
                    reg.deeplearning.cn/ayers/superbrain-pytorch:1.7-cuda10.2-cudnn7-devel-ubuntu16.04-final \
                    bash /root/scripts/scripts_st_e2e/$config_shell $sourcefile $targetfile $outputdir
```

where `$config_shell` is the shell to shell for each configuration to be run, `$sourcefile` is the input audio file to be translated,  `$targetfile` is the reference file ,which will be used for calculate BLEU and AL,  `$outputdir` is the output directory for restore `intances.log` and results scores.




#### Config and Results

This part provides short introduction for `$config_shell`, then give the results on MUSTC-v2 tst-common test set for segmentation and and the results on IWSLT tst2018 test sets for unsegmentation.

- **Low-latency config:** 
  1. Segmentation: `$config_shell=low_seg.sh`
  2. Unegmentation: `$config_shell=low_unseg.sh`
- **Medium-latency config:** 
  1. Segmentation: `$config_shell=mid_seg.sh`
  2. Unegmentation: `$config_shell=mid_unseg.sh`
- **High-latency config:** 
  1. Segmentation: `$config_shell=high_seg.sh`
  2. Unegmentation: `$config_shell=high_unseg.sh`

The following table presents the results on `MUSTCv2-tst-common` test set by segmentation way:

| End2End single  model | BLEU  | AL      | AL_CA   | AP   | AP_CA | DAL     | DAL_CA  |
| --------------------- | ----- | ------- | ------- | ---- | ----- | ------- | :-----: |
| low latency           | 26.95 | 944.55  | 1936.28 | 0.68 | 1.04  | 1451.94 | 3085.37 |
| medium latency        | 28.03 | 1829.96 | 3036.49 | 0.82 | 1.13  | 2713.55 | 4049.27 |
| high latency          | 28.88 | 3901.7  | 5308.26 | 0.95 | 1.32  | 4721.16 | 6444.71 |

The following table presents the results on `IWSLT tst2018` test set by unsegmentation way:

| End2End single  model | BLEU  | Segment-BLEU |  AL   | AL_CA  | AP   | AP_CA |  DAL  | DAL_CA |
| :-------------------: | :---: | :----------: | :---: | :----: | ---- | :---: | :---: | ------ |
|      low latency      | 21.51 |    17.33     | 57508 | 219381 | 0.5  |  0.7  | 32163 | 268166 |
|    medium latency     | 22.57 |    18.75     | 36396 | 191402 | 0.5  | 0.69  | 30246 | 237926 |
|     high latency      | 22.93 |     19.1     | 41867 | 177120 | 0.5  | 0.669 | 39156 | 202430 |

### System 2: End-to-End model ensemble

The following is the template command for all configurations in system 2.

```shell
docker run --rm -it -v $ROOT_DIR/modelfile/:/root/modelfile/ \
                    -v $ROOT_DIR/scripts/:/root/scripts/ \
                    reg.deeplearning.cn/ayers/superbrain-pytorch:1.7-cuda10.2-cudnn7-devel-ubuntu16.04-final \
                    bash /root/scripts/scripts_st_e2e/$config_shell $sourcefile $targetfile $outputdir
```

#### Config and Results

This part provide short introduction for `$config_shell`, then give the results on MUSTC-v2 tst-common test set for segmentation and and the results on IWSLT tst2018 test sets for unsegmentation.

- **Low-latency config:** 
  1. Segmentation: `$config_shell=low_seg_ens.sh`
  2. Unegmentation: `$config_shell=low_unseg_ens.sh`
- **Medium-latency config:** 
  1. Segmentation: `$config_shell=mid_seg_ens.sh`
  2. Unegmentation: `$config_shell=mid_unseg_ens.sh`
- **High-latency config:** 
  1. Segmentation: `$config_shell=high_seg_ens.sh`
  2. Unegmentation: `$config_shell=high_unseg_ens.sh`

The following table presents the results on `MUSTCv2-tst-common` test set by segmentation way:

| End2End model ensemble | BLEU  | AL      | AL_CA   | AP   | AP_CA | DAL     | DAL_CA   |
| ---------------------- | ----- | ------- | ------- | ---- | ----- | ------- | -------- |
| low latency            | 27.40  | 922.91  | 2674.35 | 0.68 | 1.56  | 1419.33 | 5498.09  |
| medium latency         | 29.56 | 1971.73 | 5091.7  | 0.83 | 1.97  | 2825.92 | 7351.59  |
| high latency           | 30.00  | 3724.99 | 7810.85 | 0.95 | 2.26  | 4639.84 | 10241.98 |

The following table presents the results on `IWSLT tst2018` test set by unsegmentation way:

| End2End  model ensemble | BLEU  | Segment-BLEU | AL       | AL_CA    | AP   | AP_CA | DAL      | DAL_CA |
| :---------------------: | ----- | :----------: | -------- | -------- | ---- | ----- | -------- | ------ |
|       low latency       | 22.5  |    18.41     | 27871.37 | 363232.9 | 0.49 | 1.17  | 32523.92 | 816760 |
|     medium latency      | 23.6  |    20.13     | 29683    | 322654.4 | 0.49 | 1.08  | 28307    | 695555 |
|      high latency       | 23.63 |    20.21     | 37794    | 330989   | 0.5  | 1.06  | 37240    | 663756 |

### System 3: Pipeline systems with  models ensembled

The following is the template command for all configurations in system 3.

```shell
docker run --rm -it -v $ROOT_DIR/modelfile/:/root/modelfile/ \
                    -v $ROOT_DIR/scripts/:/root/scripts/ \
                    reg.deeplearning.cn/ayers/superbrain-pytorch:1.7-cuda10.2-cudnn7-devel-ubuntu16.04-final \
                    bash /root/scripts/scripts_st_ppl/$config_shell $sourcefile $targetfile $outputdir
```

#### Config and Results

This part provides short introduction for `$config_shell`, then give the results on MUSTC-v2 tst-common test set for segmentation and and the results on IWSLT tst2018 test sets for unsegmentation.

- **Medium-latency config:** 
  1. Segmentation: `$config_shell=st_ppl_en_de_transducer_ensemble_medium.sh`
  2. Unegmentation: `$config_shell=st_ppl_en_de_transducer_unseg_medium.sh`
- **High-latency config:** 
  1. Segmentation: `$config_shell=st_ppl_en_de_transducer_ensemble_high.sh`
  2. Unegmentation: `$config_shell=st_ppl_en_de_transducer_unseg_high.sh`

The following table presents the results on `MUSTCv2-tst-common` test set by segmentation way:

| Pipeline model ensemble | BLEU  | AL      | AL_CA   | AP   | AP_CA | DAL     | DAL_CA  |
| ----------------------- | ----- | ------- | ------- | ---- | ----- | ------- | ------- |
| medium latency          | 29.68 | 1861.14 | 4718.11 | 0.82 | 1.97  | 2649.87 | 7498.40 |
| high latency            | 30.75 | 2737.72 | 6470.47 | 0.90 | 2.00  | 3628.73 | 8104.76 |

The following table presents the results on `IWSLT tst2018` test set by unsegmentation way:

| pipeline model ensemble | BLEU  | Segment-BLEU | AL       | AL_CA     | AP   | AP_CA | DAL      | DAL_CA    |
| ----------------------- | ----- | ------------ | -------- | --------- | ---- | ----- | -------- | --------- |
| medium latency          | 24.99 | 21.12        | 8318.62  | 327580.41 | 0.5  | 1.11  | 28526.70 | 742663.53 |
| high latency            | 26.06 | 21.98        | 27705.01 | 305211.70 | 0.5  | 0.99  | 29869.41 | 598365.09 |

