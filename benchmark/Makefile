#  MIPLearn: Extensible Framework for Learning-Enhanced Mixed-Integer Optimization
#  Copyright (C) 2020, UChicago Argonne, LLC. All rights reserved.
#  Released under the modified BSD license. See COPYING.md for more details.
#  Written by Alinson S. Xavier <axavier@anl.gov>

CHALLENGES := \
    stab/ChallengeA \
    knapsack/ChallengeA \
    tsp/ChallengeA

main: $(addsuffix /performance.png, $(CHALLENGES))

%/train_instances.bin:
	python benchmark.py train $*

%/benchmark_baseline.csv: %/train_instances.bin
	python benchmark.py test-baseline $*

%/benchmark_ml.csv: %/benchmark_baseline.csv
	python benchmark.py test-ml $*

%/performance.png: %/benchmark_ml.csv
	python benchmark.py charts $*

clean:
	rm -rvf stab knapsack

clean-ml:
	rm -rvf */*/benchmark_ml.csv

clean-charts:
	rm -rfv */*/performance.png

.PHONY: clean clean-ml clean-charts
.SECONDARY:
