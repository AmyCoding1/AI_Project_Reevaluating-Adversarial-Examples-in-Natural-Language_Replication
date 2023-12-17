# Replication of the experiments of the paper: "Reevaluating Adversarial Examples in Natural Language"

This repository contains code and datasets to replicate the experiments in "Reevaluating Adversarial Examples in Natural Language."

## Files

### Section 3
- `section_3_case_study` includes the datasets and survey results used for human studies of semantics of adversarial examples generated by Alzantot and TextFooler attacks. See `section_3_case_study/semantic/` for Jupyter notebooks containing analyses of results that correspond to Section 4.1 of the paper.
	- Semantics replication is conducted using the answers from the students of the class
	- Grammaticality studies are conducted using the [`language_tool_python`](https://github.com/jxmorris12/language_tool_python) grammar checker.
	- Grammaticality experiments are replicated with a reduced number of examples, due to the time constraint and GPU availability in Coolab.
	- Grammaticality experiment has been replicated using TEXTFOOLER attack in BERT model in the movie_review dataset of the experiment.
	- Non-suspicion experiment was not able to be replicated due to the issues with GROVER model, it will be replicated with TFADJUSTED attack in Section 6.


### Section 5

To generated adjusted exmaples using TFAdjusted's attack recipe, see `section_6_adjusted_attacks/recipes/textfooler_2019_jin_adjusted.py` 

#### 5.1 Adjusted Constraint Application

- `section_5_tfadjusted/` contains the survey results and analysis for non-suspicion of adversarial examples generated using TFAdjusted

#### 5.2 Adversarial Training
- `section_5_adv_training/` contains code for the adversarial training experiments in Section 5.2 of the paper. This folder contains file to replicate receipes attacks from Section 6.

### Section 6
- `section_6_adjusted_attacks/` contains code for running the adjusted Alzantot and TextFooler attacks as well as their survey results.
	- `./recipes` contains the attack recipes for AlzantotAdjusted and TFAdjusted, which can be run using [TextAttack](https://github.com/QData/TextAttack),
	- The receipes of this section are used to do adversarial training with higher quality examples for Section 5.2 of the paper.
  
### Running the attacks with adjusted thresholds

Both attack recipes in `section_6_adjusted_attacks/recipes/*.py` have been runned by installing TextAttack and using its `--attack-from-file parameter`. 

To run AlzantotAdjusted on 5 samples from the MR datase against TextAttack's default bert-base-uncased model fine-tuned on MR, run the following command: 
``` bash
textattack attack --model bert-base-uncased-mr --attack-from-file section_6_adjusted_attacks/recipes/alzantot_2018_adjusted.py --num-examples 5
```

Or to run TFAdjusted on 5 examples on an LSTM fine-tuned for AGNews:
```bash
textattack attack --model lstm-ag-news --attack-from-file section_6_adjusted_attacks/recipes/textfooler_jin_2019_adjusted.py --num-examples 5
```

These attacks have been tested using textattack==0.3.9
### Appendix
- `appx_1.2_finding_thresholds` contain the results from the 'threshold-finding' experiments from the paper.
	- `syn_thresh` contains the synonyms used in the survey to find the threshold for word embedding cosine similarity in the counter-fitted embedding space. Human responses indicated that $0.9$ was the optimal threshold for counter-fitted embedding word cosine similarity.
	- `se_thresh` contains the code, generated data, and survey results for finding the USE Sentence Encoding similarity that best preserved semantics. For analysis of results, see `se_thresh/results/se_threshold_analysis_results`. Survey responses indicated that a USE cosine similarity threshold of $0.98$ preserved semantics without being overly restrictive.
	

## Citation

+ Title: Reevaluating Adversarial Examples in Natural Language 
+ Venue: 2020 EMNLP: 2020 Conference on Empirical Methods in Natural Language Processing Findings 
+ ArXiv Link: https://arxiv.org/abs/2004.14174
+ Authors: John X. Morris, Eli Lifland, Jack Lanchantin, Yangfeng Ji, Yanjun Qi
+ Abstract: State-of-the-art attacks on NLP models have different definitions of what constitutes a successful attack. These differences make the attacks difficult to compare. We propose to standardize definitions of natural language adversarial examples based on a set of linguistic constraints: semantics, grammaticality, edit distance, and non-suspicion. We categorize previous attacks based on these constraints. For each constraint, we suggest options for human and automatic evaluation methods. We use these methods to evaluate two state-of-the-art synonym substitution attacks. We find that perturbations often do not preserve semantics, and 45\% introduce grammatical errors. Next, we conduct human studies to find a threshold for each evaluation method that aligns with human judgment. Human surveys reveal that to truly preserve semantics, we need to significantly increase the minimum cosine similarity between the embeddings of swapped words and sentence encodings of original and perturbed inputs. After tightening these constraints to agree with the judgment of our human annotators, the attacks produce valid, successful adversarial examples. But quality comes at a cost: attack success rate drops by over 70 percentage points. Finally, we introduce TextAttack, a library for adversarial attacks in NLP.



```
@article{morris2020reevaluating,
  title={Reevaluating Adversarial Examples in Natural Language},
  author={Morris, John X and Lifland, Eli and Lanchantin, Jack and Ji, Yangfeng and Qi, Yanjun},
  journal={arXiv preprint arXiv:2004.14174},
  year={2020}
}
```









# AI_Project_Reevaluating-Adversarial-Examples-in-Natural-Language_Replication
# AI_Project_Reevaluating-Adversarial-Examples-in-Natural-Language_Replication
# AI_Project_Reevaluating-Adversarial-Examples-in-Natural-Language_Replication