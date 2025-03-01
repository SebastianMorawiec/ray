.. include:: /_includes/rllib/we_are_hiring.rst

.. _rllib-index:

RLlib: Industry-Grade Reinforcement Learning
============================================

.. toctree::
    :hidden:

    rllib-training
    key-concepts
    rllib-env
    rllib-algorithms
    user-guides
    rllib-examples
    package_ref/index


.. image:: images/rllib-logo.png
    :align: center

**RLlib** is an open-source library for reinforcement learning (RL),
offering support for
production-level, highly distributed RL workloads while maintaining
unified and simple APIs for a large variety of industry applications.
Whether you would like to train your agents in a **multi-agent** setup,
purely from **offline** (historic) datasets, or using **externally
connected simulators**, RLlib offers a simple solution for each of your decision
making needs.

If you either have your problem coded (in python) as an
`RL environment <rllib-env.html#configuring-environments>`_
or own lots of pre-recorded, historic behavioral data to learn from, you will be
up and running in only a few days.

RLlib is already used in production by industry leaders in many different verticals,
such as
`climate control <https://www.anyscale.com/events/2021/06/23/applying-ray-and-rllib-to-real-life-industrial-use-cases>`_,
`industrial control <https://www.anyscale.com/events/2021/06/23/applying-ray-and-rllib-to-real-life-industrial-use-cases>`_,
`manufacturing and logistics <https://www.anyscale.com/events/2022/03/29/alphadow-leveraging-rays-ecosystem-to-train-and-deploy-an-rl-industrial>`_,
`finance <https://www.anyscale.com/events/2021/06/22/a-24x-speedup-for-reinforcement-learning-with-rllib-+-ray>`_,
`gaming <https://www.anyscale.com/events/2021/06/22/using-reinforcement-learning-to-optimize-iap-offer-recommendations-in-mobile-games>`_,
`automobile <https://www.anyscale.com/events/2021/06/23/using-rllib-in-an-enterprise-scale-reinforcement-learning-solution>`_,
`robotics <https://www.anyscale.com/events/2021/06/23/introducing-amazon-sagemaker-kubeflow-reinforcement-learning-pipelines-for>`_,
`boat design <https://www.youtube.com/watch?v=cLCK13ryTpw>`_,
and many others.

RLlib in 60 seconds
-------------------

.. figure:: images/rllib-index-header.svg

It only takes a few steps to get your first RLlib workload
up and running on your laptop.

RLlib does not automatically install a deep-learning framework, but supports
**TensorFlow** (both 1.x with static-graph and 2.x with eager mode) as well as
**PyTorch**.
Depending on your needs, make sure to install either TensorFlow or
PyTorch (or both, as shown below):

.. raw:: html

    <div class="termynal" data-termynal>
        <span data-ty="input">pip install "ray[rllib]" tensorflow torch</span>
    </div>

.. note::

    For installation on computers running Apple Silicon (such as M1), please follow instructions
    `here. <https://docs.ray.io/en/latest/ray-overview/installation.html#m1-mac-apple-silicon-support>`_
    To be able to run our Atari examples, you should also install
    `pip install "gym[atari]" "gym[accept-rom-license]" atari_py`.

This is all you need to start coding against RLlib.
Here is an example of running a PPO Algorithm on the
`Taxi domain <https://www.gymlibrary.dev/environments/toy_text/taxi/>`_.
We first create a `config` for the algorithm, which sets the right environment, and
defines all training parameters we want.
Next, we `build` the algorithm and `train` it for a total of `5` iterations.
A training iteration includes parallel sample collection by the environment workers, as well as loss calculation on the collected batch and a model update.
As a last step, we `evaluate` the trained Algorithm:

.. literalinclude:: doc_code/rllib_in_60s.py
    :language: python
    :start-after: __rllib-in-60s-begin__
    :end-before: __rllib-in-60s-end__

Note that you can use any Farama-Foundation Gymnasium environment as `env`.
In `rollouts` you can for instance specify the number of parallel workers to collect samples from the environment.
The `framework` config lets you choose between "tf2", "tf" and "torch" for execution.
You can also tweak RLlib's default `model` config,and set up a separate config for `evaluation`.

If you want to learn more about the RLlib training API,
`you can learn more about it here <rllib-training.html#using-the-python-api>`_.
Also, see `here for a simple example on how to write an action inference loop after training. <https://github.com/ray-project/ray/blob/master/rllib/examples/inference_and_serving/policy_inference_after_training.py>`_

If you want to get a quick preview of which **algorithms** and **environments** RLlib supports,
click on the dropdowns below:

.. dropdown:: **RLlib Algorithms**
    :animate: fade-in-slide-down

    *  High-throughput architectures

       -  |pytorch| |tensorflow| :ref:`Importance Weighted Actor-Learner Architecture (IMPALA) <impala>`

       -  |pytorch| |tensorflow| :ref:`Asynchronous Proximal Policy Optimization (APPO) <appo>`

    *  Gradient-based

       -  |pytorch| |tensorflow| :ref:`Deep Q Networks (DQN, Rainbow, Parametric DQN) <dqn>`

       -  |pytorch| |tensorflow| :ref:`Proximal Policy Optimization (PPO) <ppo>`

       -  |pytorch| |tensorflow| :ref:`Soft Actor Critic (SAC) <sac>`

    *  Model-based / Meta-learning / Offline

       -  |pytorch| :ref:`DreamerV3 <dreamerv3>`

    *  Offline

       -  |pytorch| |tensorflow| :ref:`Conservative Q-Learning (CQL) <cql>`
       -  |pytorch| |tensorflow| :ref:`Advantage Re-Weighted Imitation Learning (MARWIL) <marwil>`


.. dropdown:: **RLlib Environments**
    :animate: fade-in-slide-down

    *  `RLlib Environments Overview <rllib-env.html>`__
    *  `Farama-Foundation gymnasium <rllib-env.html#gymnasium>`__
    *  `Vectorized <rllib-env.html#vectorized>`__
    *  `Multi-Agent and Hierarchical <rllib-env.html#multi-agent-and-hierarchical>`__
    *  `External Agents and Applications <rllib-env.html#external-agents-and-applications>`__

       -  `External Application Clients <rllib-env.html#external-application-clients>`__

    *  `Advanced Integrations <rllib-env.html#advanced-integrations>`__

Feature Overview
----------------

.. grid:: 1 2 3 3
    :gutter: 1
    :class-container: container pb-4

    .. grid-item-card::

        **RLlib Key Concepts**
        ^^^
        Learn more about the core concepts of RLlib, such as environments, algorithms and
        policies.
        +++
        .. button-ref:: rllib-core-concepts
            :color: primary
            :outline:
            :expand:

            Key Concepts

    .. grid-item-card::

        **RLlib Algorithms**
        ^^^
        Check out the many available RL algorithms of RLlib for model-free and model-based
        RL, on-policy and off-policy training, multi-agent RL, and more.
        +++
        .. button-ref:: rllib-algorithms-doc
            :color: primary
            :outline:
            :expand:

            Algorithms

    .. grid-item-card::

        **RLlib Environments**
        ^^^
        Get started with environments supported by RLlib, such as Farama foundation's Gymnasium, Petting Zoo,
        and many custom formats for vectorized and multi-agent environments.
        +++
        .. button-ref:: rllib-environments-doc
            :color: primary
            :outline:
            :expand:

            Environments


The following is a summary of RLlib's most striking features.
Click on the images below to see an example script for each of the listed features:

.. include:: feature_overview.rst


Customizing RLlib
-----------------

RLlib provides simple APIs to customize all aspects of your training- and experimental workflows.
For example, you may code your own `environments <rllib-env.html#configuring-environments>`__
in python using Farama-Foundation's gymnasium or DeepMind's OpenSpiel, provide custom
`TensorFlow/Keras- <rllib-models.html#tensorflow-models>`__ or ,
`Torch models <rllib-models.html#torch-models>`_, write your own
`policy- and loss definitions <rllib-concepts.html#policies>`__, or define
custom `exploratory behavior <rllib-training.html#exploration-api>`_.

Via mapping one or more agents in your environments to (one or more) policies, multi-agent
RL (MARL) becomes an easy-to-use low-level primitive for our users.

.. figure:: images/rllib-stack.svg
    :align: left
    :width: 650

    **RLlib's API stack:** Built on top of Ray, RLlib offers off-the-shelf, highly distributed
    algorithms, policies, loss functions, and default models (including the option to
    auto-wrap a neural network with an LSTM or an attention net). Furthermore, our library
    comes with a built-in Server/Client setup, allowing you to connect
    hundreds of external simulators (clients) via the network to an RLlib server process,
    which provides learning functionality and serves action queries. User customizations
    are realized via sub-classing the existing abstractions and - by overriding certain
    methods in those sub-classes - define custom behavior.


.. |tensorflow| image:: images/tensorflow.png
    :class: inline-figure
    :width: 16

.. |pytorch| image:: images/pytorch.png
    :class: inline-figure
    :width: 16
