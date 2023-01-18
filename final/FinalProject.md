# ECE 522 Final Project - Dynamic Model Development in ANDES

## Introduction

In ANDES, a hybrid symbolic-numeric framework is proposed to enable fast prototyping. The proposed framework aims to make modleing *as simple as describing equations*[^1]. In the final project, you will develop realistic dynamic models in ANDES.

## Project Tasks

### Model Prepration

The candidate models include ESAC2A, ESAC3A, ESAC4A, ESAC6A, AC7B, AC8B, DC3A, ESST2A. They are excitation system models selected from [WECC Approved Dynamic Model Library](https://www.wecc.org/Reliability/Approved%20Dynamic%20Models%20May%202022.pdf). You need to pick one model to develop as your final project.

Before implementing the model in ANDES, you will need to collect necessary materials of the selected model. The materials involve **model parameters** and **block diagrams**, and they can be found from PSS/E document, PowerWorld document, and Neplan document.

### Model Development

You can go through the [Model reference - Exciter](https://docs.andes.app/en/latest/groupdoc/Exciter.html) to find a similar exciter as reference code.

After that, you can start to play with the model development as follow:

1. Create a branch with the name of developed model from the most recent develop branch by command: ``git checkout -b [MODEL_NAME] develop``
2. Find similar function pieces from existing models to reduce manual efforts. During the development, you are encouraged to look up the modeling pieces in the [Development](https://docs.andes.app/en/latest/modeling/index.html#development), such as Group, Models, Parameters, and Variables.
3. Build your model and finalize it.
4. Re-generate the pycode by `andes prep`. Sometimes there occur multi-functionalities, where you may need `andes prep -f` to re-generate all model codes.
5. Create a test system that includes your model, where the IEEE 14-bus system ``ieee14/ieee14_ace.xlsx`` can be a good basecase.
6. Load the test case, and run the `ss.TDS.init()` to see if the initialization is successful. If initialization runs into an error, you may need to tune the model initialization equations (`v_str` defined in the model). Remember to run `andes prep` and restart the kernel every time you make a change to the model code.

### Model Test

In the tutorial Chapter 2, you have found the critical clearing time of the WECC system. As comparison, you can revise the WECC system by replacing some of the exciters with your model.

Then, you need to find the critical clearing time (CCT) of the revised WECC system and improve the transient stabilty by increasing the exciter gain to see if the results are reasonable.

### Project Report

In the last, a final report is required as the summary of the project. [IEEE - Manuscript Templates for Conference Proceedings](https://www.ieee.org/conferences/publishing/templates.html) is used, and a copy is available at ``/final/conference-template-a4.docx``.

In the report, required sections include Introduction, Model Development, Model Test, and Conclusion.

## Submission

You need to submit the **PROJECT REPORT** with **FORMATTED** name `FirstName_LastName_NetID_Report.docx`, for example, `Tim_Cook_tcook3_Report.docx`.

**EMAIL** the report to Dr. Kevin Tomsovic (tomsovic@utk.edu) with title "ECE522 Report" and cc Jinning Wang (jwang175@vols.utk.edu). You should receive a feedback email to confrim the submission.

## Advance Development

### Refactoring

> [techtarget.com](https://www.techtarget.com/searchapparchitecture/definition/refactoring#:~:text=Refactoring%20is%20the%20process%20of,altering%20the%20code%27s%20external%20behavior.): Refactoring is the process of resturcturing code, while not changing its original functionality.

In power system modeling, there are usually several functions shared by the models in a same group. For example, excitation system is designed to support the excitation voltage for synchronous generators.

In ANDES, the common code for ``Exciter`` includes parameters ``u``, ``name``, ``syn`` and variables ``vout``, ``vi``. See [Model reference - Exciter](https://docs.andes.app/en/latest/groupdoc/Exciter.html#exciter) for detailed documentation.

However, simply repeating common parts in newly developed exciter model challenges the readability and maintainability. Given ANDES has more than 17 exciter models, it will be a disater if new parameters or variables need to be included into the *Group Exciter*.

To address this issue, it is preferred to introduce a new class ``ExcBase`` that holds the common parts.

### Model Quality

A good model implementation should be readable and maintainable. As such, your code needs to follow readable code style such as [PEP 8 - Style Guide for Python Code](https://peps.python.org/pep-0008/).

A clear documentation and a detailed demonstration of the model are also helpful for the software maintainance. See demonstration and documentation of [Demonstration - DGPRCT1](https://github.com/cuihantao/andes/tree/master/examples/demonstration) and [Model reference - DGPRCT1](https://docs.andes.app/en/latest/groupdoc/DGProtection.html#dgprct1).

### Model Contribution

ANDES is an open-source software that benefits a lot from the open-source community. See [GitHub contributors](https://github.com/cuihantao/andes/graphs/contributors) for the contributor list.

It is highly encouraged to contribute your model to the [ADNES repository](https://github.com/cuihantao/andes) by opening a pull request (PR).

[^1]: H. Cui, F. Li and K. Tomsovic, "Hybrid Symbolic-Numeric Framework for Power System Modeling and Analysis," in IEEE Transactions on Power Systems, vol. 36, no. 2, pp. 1373-1384, March 2021, doi: 10.1109/TPWRS.2020.3017019.
