---
title: LightGBM
---

# LightGBM

## Advantages
LightGBM loads the best model after early stopping (in contrast to
XGBoost). See here:
<https://lightgbm.readthedocs.io/en/latest/Python-Intro.html#early-stopping>

## Hyperparameter
Useful hyperopt search space:

``` python
space = {
        'num_leaves' : hp.quniform('num_leaves', 100, 600, 10),
        'min_data_in_leaf' : hp.quniform('min_data_in_leaf', 10, 30, 1),
        'max_bin' : hp.quniform('max_bin', 200, 2000, 10),
        'bagging_fraction' : hp.uniform('bagging_fraction', 0.01, 1.0),
        'bagging_freq' : hp.quniform('bagging_freq', 0, 10, 1),
        'feature_fraction' :  hp.uniform('feature_fraction', 0.5, 1.0),
        'lambda_l2' : hp.uniform('lambda_l2', 0.0, 70.0),
        'min_gain_to_split' : hp.uniform('min_gain_to_split', 0.0, 2.0),
        }
```

## Links
  - Root Documentation:
    <https://lightgbm.readthedocs.io/en/latest/index.html>
      - Python API:
        <https://lightgbm.readthedocs.io/en/latest/Python-API.html>
      - Parameters:
        <https://lightgbm.readthedocs.io/en/latest/Parameters.html>
      - Parameters Tuning:
        <https://lightgbm.readthedocs.io/en/latest/Parameters-Tuning.html>
      - Early Stopping:
        <https://lightgbm.readthedocs.io/en/latest/Python-Intro.html#early-stopping>
      - Load and save the booster:
        <https://lightgbm.readthedocs.io/en/latest/Python-Intro.html#training>
      - Regression Example:
        <https://github.com/Microsoft/LightGBM/tree/master/examples/regression>
      - Binary Classification Example:
        <https://github.com/Microsoft/LightGBM/tree/master/examples/binary_classification>
      - Multiclass Classification Example:
        <https://github.com/Microsoft/LightGBM/tree/master/examples/multiclass_classification>
      - GPU Tutorial:
        <https://lightgbm.readthedocs.io/en/latest/GPU-Tutorial.html>
  - Parameter overview with filter:
    <https://sites.google.com/view/lauraepp/parameters>

## GPU Support
  - Build with GPU Support: `python setup.py install --gpu
    --opencl-include-dir=/usr/local/cuda/include/
    --opencl-library=/usr/local/cuda/lib64/libOpenCL.so`
  - Install with GPU Support: `pip install lightgbm
    --install-option=--gpu
    --install-option=--opencl-include-dir=/usr/local/cuda/include/
    --install-option=--opencl-library=/usr/local/cuda/lib64/libOpenCL.so`

To use the GPU you have to provide `'device_type': 'gpu'` to parameters.
