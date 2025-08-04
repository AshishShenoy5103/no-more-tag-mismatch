# Maven Dependency Resolution Fix

This repository provides a quick fix for the common Maven error:

`Non-resolvable import POM: io.netty:netty-bom:pom:4.1.122.Final failed to transfer`  
`Could not transfer artifact from.to central (https://repo.maven.apache.org/maven2): Tag mismatch`


### ❓ Problem

Maven was unable to resolve certain dependencies due to cached metadata or update policy restrictions.

You might see errors like:
- **Tag mismatch**
- **Resolution is not reattempted until the update interval of central has elapsed**

### 🛠️ Solution

We fix this issue by updating the Maven `settings.xml` file to:
- Force Maven to always check for updated dependencies
- Add a mirror to ensure connection to a reliable Maven Central

### 🔧 How to Use

1. Replace your `~/.m2/settings.xml` with [this one](./settings.xml) or create a new one if it doesn’t exist.

2. Make sure it includes:

```xml
<updatePolicy>always</updatePolicy>
```

3. Run the following command in your project directory:
```bash
mvn clean install -U
```

This will:  
- Clear old caches
- Force Maven to re-download everything fresh  

📁 Files in This Repo
- `settings.xml`: The fixed configuration for Maven
- `README.md`: You’re reading it

---

💬 Credits  
Tested and fixed by me after hours of Maven debugging frustration

---

If this helped you, consider starring ⭐ the repo or sharing it with your team!

---

