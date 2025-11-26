# PROCESS-Jenkins-Pipeline-with-Input-Step-Post-Build-Multiple-Stages
📘 Explanation of the Full Process (Step-by-Step)

1️⃣ Created a Pipeline Job

I created a new Pipeline job in Jenkins and selected Pipeline script.

2️⃣ Implemented Three Stages

I added three stages:

✔️ Stage 1 — code

Purpose: Represent the code checkout or preparation step.

stage("code") {
    steps {
        echo "this is code stage"
    }
}

✔️ Stage 2 — build

Purpose: Represent the build step (maven/gradle/compile).

stage("build") {
    steps {
        echo "this is code stage"
    }
}

✔️ Stage 3 — deploy

This stage contains the manual approval input step.

3️⃣ Added Input Step (Manual Approval)

Before running the deploy stage, I added:

input {
    message "can i deploy"
}

Why?

Pipeline pauses here

Jenkins waits for user approval

Once you click Proceed, the deploy stage runs

This simulates a real production approval process.

4️⃣ Added Post-Build Step

In the post block, I added:

post {
    always {
        echo "this will be printed any ways"
    }
}

Meaning:

This message prints always

Whether pipeline succeeds, fails, or is aborted

###Post section is used for:

Notifications

Cleanup

Status messages

### Complete Working Flow

This is the actual working sequence of your pipeline:

Code stage runs

Build stage runs

Pipeline reaches deploy stage

Jenkins shows a popup: "can I deploy?"

You click Proceed

Deploy stage executes

Post-build message prints:
"this will be printed any ways"
