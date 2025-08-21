# AutoCodeRover Jetbrains Plugin

**AutoCodeRover (ACR)** is a fully automated approach for resolving GitHub issues (bug fixing and feature addition) where LLMs are combined with analysis and debugging capabilities to prioritize patch locations ultimately leading to a patch.

**AutoCodeRover IDE Plugin (ACR Plugin)** brings **AutoCodeRover Agent** - an **autonomous program improvement** directly into developer's Integrated Development Environment (IDE). Using this IDE extension, developers can benefit from an agent with autonomous improvement capabilities in common development events inside the IDE, such as fixing a bug, adding a feature, build failure troubleshooting, test failure diagnosis, and code-quality checks.

## Features
- **Fix a bug**: Prompt ACR Agent to fix a bug in your code.
- **Add a feature**: Prompt ACR Agent to add a feature to your code.
- **Build failure troubleshooting**: Prompt ACR Agent to troubleshoot build failures.
- **Test failure diagnosis**: Prompt ACR Agent to diagnose test failures.
- **Code-quality checks**: Run SonarLint to check code quality issues and prompt ACR Agent to fix them.

## Prerequisites
- IntelliJ IDEA 2022.2.5 or later.
- JDK 17 or later.

## Download
To download the plugin:
1. Clone the repository or download the ZIP file from the releases section on GitHub.
    ```bash
    git clone https://github.com/AutoCodeRoverSG/jetbrains-plugin.git
    ```
2. Build the plugin using the following command:
    ```bash
    ./gradlew buildPlugin
    ```
3. The plugin ZIP file will be generated in the `build/distributions/` directory.

## Running the Plugin in Development Mode

If you want to run the plugin in a test IntelliJ IDEA instance:

1. Open a terminal in the project directory.
2. Run the following command to launch a clean, isolated IntelliJ IDEA environment:
    ```bash
    ./gradlew runIde
    ```
3. The test IDE instance will launch without automatically installing the plugin.
4. Follow the steps under "Installation" to manually install the plugin in the test environment.


## Installation
To install the plugin in IntelliJ IDEA:

1. Open IntelliJ IDEA.
2. Navigate to `File > Settings > Plugins` (or `IntelliJ IDEA > Preferences > Plugins` on macOS).
3. Click the gear icon (⚙️) and choose `Install Plugin from Disk...`.
4. Navigate to the `build/distributions/` directory in your project folder.
5. Select the `jetbrains-plugin-ACR-1.0.zip` file.
6. Click `OK` to install the plugin.
7. Restart IntelliJ IDEA to activate the plugin.

## Setup
Once the plugin is installed:

1. Go to `File > Settings > AutoCodeRover Plugin Settings`.
2. Necessary settings:
    - **AutoCodeRover Authentication Token**: Enter your ACR Auth Token. You can generate an Auth Token from the [AutoCodeRover WebConsole](https://uat.autocoderover.dev/).
    - **AutoCodeRover API Domain**: Enter the API domain for ACR. The default is `https://uat.autocoderover.dev/`.
    - **Project ID**: Enter the project ID for your ACR project. You can find this from the [AutoCodeRover WebConsole](https://uat.autocoderover.dev/project/index) `Projects` page when you create a new project.
    - **LLM Key Name**: Enter the key name for the LLM that you set up on the [AutoCodeRover WebConsole](https://uat.autocoderover.dev/user/account) `User` page.
    - **Provider**: Select the provider for the LLM. (e.g., `OpenAI`).
    - **Model**: Select the corresponding model you want to use (e.g., `gpt-4o`).
3. Click `Apply` and `OK` to save your settings.

## Workflow

After setting up the plugin, you can start enjoying AutoCodeRover agentic support with your development tasks directly within Jetbrains IDEs. Here’s how to get started:

### Opening the ACR Plugin

1. **Open the Tool Window**:
Click on the "AutoCodeRover Assistant" tab on the right-hand side of your IDE window.

2. **Understanding the Interface**:
    - The UI of ACR Plugin is divided into three main sections:
        - **Chat History**: This area displays the conversation between you and the AutoCodeRover Agent.
        - **Input Area**: At the bottom, you'll find the input box where you can type messages.
        - **Button Panel**: Besides the input area, there are buttons for various actions.
          - Send / Stop an ACR Run
          - Reset chat history
          - Trigger SonarLint analysis
          

### Fix a Bug / Add a Feature

In the chat history, you'll see two main buttons that you can use to interact with the AutoCodeRover Agent:

1. **Fix a Bug**:
    - Use this button to get help with fixing bugs in your code.
    - When you click this button:
        1. ACR Plugin will prompt you to describe the issue.
        2. Simply clicking on the `send` button, ACR Plugin will prompt ACR Agent to analyze the code and provide a potential fix.

2. **Add a Feature**:
    - Use this button when you need help generating code for a new feature.
    - When you click this button:
       1. ACR Plugin will prompt you to describe the feature.
       2. Simply clicking on the `send` button, ACR Plugin will prompt ACR Agent to analyze the code and provide a potential fix.

#### 🎥 Demo Video
Watch the full demonstration of prompting ACR Agent to fix a bug / add a feature:

https://github.com/user-attachments/assets/3835ca8b-5ae2-48b6-8c63-42a3862e4120

### Build Failure Troubleshooting

When a build failure event occurs inside your IDE, ACR Plugin will automatically capture and display the `build error log` in the UI, followed by buttons for you to prompt ACR Agent for a fix.

### Test Failure Diagnosis

When a test failure event occurs inside your IDE, ACR Plugin will automatically capture and display the `test error log` in the UI, followed by buttons for you to prompt ACR Agent for a fix.

#### 🎥 Demo Video
Watch the full demonstration of prompting ACR Agent to diagnose a test failure:

https://github.com/user-attachments/assets/59959cde-46d7-4f50-b5c6-10a89c92396b

### Code-Quality Checks

AutoCodeRover Plugin integrates SonarLint to help you detect and fix code-quality issues directly inside the IDE.
1. **Run SonarLint**:
   - Click the **"Run SonarLint"** button in the plugin UI to perform static code analysis on your Java files.

2. **View Results**:
   - Issues are displayed in an expandable tree menu, grouped by file (Clicking on the file path will open the file in the editor). 
   - Each issue includes:
      - Violation message
      - Violated rule key
      - Suggested fix (if any)

3. **Prompt ACR Agent**
   - Click **"Run"** next to an individual issue to ask ACR Agent for a fix.
   - Use the **checkboxes** to select multiple issues across files and click **"Run All"** to queue batch fixes.

4. **Track Progress Live**
   - While ACR Agent is processing, the UI shows a **spinner** and highlights the active issue.
   - Success or failure is indicated via ✔️ or ❌ icons next to each issue once resolved.

#### 🎥 Demo Video
Watch the full demonstration of prompting ACR Agent to fix SonarLint issues:

https://github.com/user-attachments/assets/b8ba286c-ad01-4ecd-afbb-0ee53431962b


## After an ACR Agent Run

Once AutoCodeRover completes its run, the plugin displays both the intermediate reasoning steps and the final patch suggestion in the chat interface. This section outlines all the actions you can take after receiving a response.

### 1. Reviewing and Providing Feedback

#### a. AutoCodeRover Response Details

- Click on **"AutoCodeRover Response Details"** to expand the panel showing all intermediate outputs from each Agent.
- Each step is displayed as a collapsible row, including:
   - Agent name (e.g., `Context Retrieval Agent`)
   - Agent subtype (e.g., `Model response (API selection)`)
   - Full output text

- Next to each model-generated response, click the **💬 feedback** icon to provide feedback.
   - Feedback is tied to the specific Agent and the model response.
   - Submitted feedback is sent back to the ACR Agent.

#### b. Quick Feedback on the Patch

- In the patch bubble, click the **💬 feedback** icon to leave direct comments on the patch.

### 2. Applying the Patch

After reviewing the Patch, you'll see two buttons:

- **Apply**: Applies the suggested Patch to your current editor.
   - The Patch is parsed and applied file by file.
   - If your local code has diverged from ACR’s baseline (the latest pushed commit) such that the Patch cannot be applied directly, ACR Plugin triggers **Patch Alignment**:
      - Non-conflicting changes are auto-merged.
      - Any conflicts are highlighted for manual inspection.
   - Modified files are opened automatically.
   - Changed lines are **temporarily highlighted** for quick visual reference.

- **Not Apply**: Dismisses the Patch. It remains in your chat history but will not modify your code.

#### 🎥 Demo Video
Watch the full demonstration of ACR Plugin performs Patch Alignment:

https://github.com/user-attachments/assets/6bd7c353-df3b-4af5-8534-b872e23030ea

### 3. Rating the Patch

At the top-right of the patch bubble:

- Click **👍** to rate the patch as helpful.
- Click **👎** to indicate dissatisfaction.

Your rating is sent to the ACR WebConsole, helping the ACR team to collect user's satisfaction ratings and improve the system.

---

These post-run features support a human-in-the-loop development experience by allowing you to:
- Understand and trace the reasoning steps,
- Provide feedback to improve future runs,
- Apply or reject fixes confidently, and
- Help train the system through direct ratings.


## Troubleshooting
If you encounter any issues:
- Ensure you have the correct version of IntelliJ IDEA and JDK installed.
- Check the IntelliJ logs (`Help > Show Log in Explorer/Finder`) for any errors.
- Refer to the official [Jetbrains Plugin Development Guide](https://plugins.jetbrains.com/docs/intellij/welcome.html) for additional help.

---

For more information, contact us at [zanwen@u.nus.edu](mailto:zanwen@u.nus.edu) or visit our website [https://autocoderover.dev/](https://autocoderover.dev/).
