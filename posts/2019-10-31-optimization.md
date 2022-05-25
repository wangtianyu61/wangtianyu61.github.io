---
layout: post
title: 优化理论与方法杂记
date: 2019-10-31
categories: blog
tags: [数学规划,运筹学]
description: 
---
这学期结束会更新【感觉NUS的optimization还是挺强的】

记录下整个体系的大概，只能以关键词了。如有不对请指出。

## 经典理论方法
### 从单纯形法说起的线性规划
Simplex method
### 互补松弛与KKT:深刻的对偶理论
对偶单纯形

互补松弛

FJ condition --> KKT condition

Lagrange Duality
### 整数规划、组合优化与理论计算机杂论
割平面/分支定界【MILP

匈牙利算法与匹配

图与网络流: shortest/longest path, max flow-min cut

Primal Dual Method

P NP NPC co-NP P-SPACE
### LP in P: 椭圆算法和内点法

### 局部即全部：凸优化
“优化本质区别不是线性与非线性，而是凸与非凸”

subgradient

local and global 

QP/SDP/SOCP

## 数值与近似算法
### 确定性数值方法
line search

steepest descent method/Newton/quasi-Newton/CG

penalty and augmented Lagrangian

trust-region
### 随机梯度下降到各种启发式算法
随机梯度下降

模拟退火/蚁群/基因
### DP in NP 
dynamic programming

approximation method/FPTAS

local search
## 数据时代下的优化
### 花开并蒂：随机优化v.s.鲁棒优化
data uncertainty: Stochastic Programming/Robust Optimization/Fuzzy Optimization

decomposition (generated columns/delayed columns)

Linear Decision Rule

Sample Average Approximation

Robust Optimization and its applications

Distributional Robust Optimization with Ambiguity Set

### 让机器学习理论回归本质
regularization

### 分布式数据与非光滑优化
parameter estimation

non-smooth and regularization

Moreau-Yosida regularization






