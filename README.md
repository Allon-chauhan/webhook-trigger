# 🔗 Configuring WebHook to Trigger CI Pipeline Automatically

## 🛠️ Technologies Used:
1. **Jenkins** 🏗️
2. **GitHub** 🐙
3. **Git** 🔧
4. **Docker** 🐳
5. **Java** ☕
6. **Maven** 📦

---

## ✅ Prerequisites:
We will be using our existing [Jenkins pipeline](https://github.com/Allon-chauhan/jenkins-cipipeline.git).

---

## 🔌 Installing Plugins in Jenkins
1. Navigate to **Manage Jenkins > Plugins**.
2. Install the following plugins:
   - **GitHub Integration Plugin**
   - **Git Plugin**
   - **Pipeline: GitHub**
   - **GitHub Branch Source Plugin**

---

## ⚙️ Configuring Jenkins Pipeline
1. We will use an **existing Freestyle Jenkins pipeline**.
2. In the pipeline configuration settings, enable:
   ```
   ✅ GitHub hook trigger for GITScm polling
   ```
   *This will trigger a build whenever a change is committed to the repository.*

---

## 🌐 Additional Setup (For Jenkins Running on Localhost)
If your **Jenkins server is running on localhost**, you'll need to expose it to GitHub using `ngrok`.

1. **Install ngrok using Homebrew**:
   ```bash
   brew install ngrok
   ```
2. **Create an ngrok account** and add your authentication token:
   ```bash
   ngrok config add-authtoken <YOUR_AUTH_TOKEN>
   ```
3. **Expose your localhost Jenkins server**:
   ```bash
   ngrok http 8080
   ```
4. **Copy the ngrok forwarding URL** (e.g., `https://randomstring.ngrok.io`) for use in GitHub WebHooks.

---

## 🔧 Configuring GitHub WebHook
1. Navigate to your repository settings on GitHub.
2. Go to **WebHooks settings**.
3. Click **Add WebHook**.
4. Set the **Payload URL** to:
   ```
   https://randomstring.ngrok.io/github-webhook/
   ```
5. Set the **Content type** to `application/json`.
6. Under **Trigger events**, choose:
   ```
   ✅ Just the push event
   ```

---

## 🧪 Testing the WebHook
1. Go to **GitHub WebHooks settings**.
2. Click **Recent Deliveries**.
3. You should start seeing **200 response codes** in the terminal where ngrok is running.

🎉 **You're all set! Your Jenkins build will now trigger automatically whenever you push changes to the repository!** 🚀
