# ⚠️ Deprecated

**Development, Issues & Pull Requests:**  
https://github.com/aa22396584/kotlin-secure-storage

**Mirrors:**  
[GitLab](https://gitlab.com/aa22396584/kotlin-secure-storage) ·
[Codeberg](https://codeberg.org/ImL1s/kotlin-secure-storage)


> This project has been moved into [web3-kmp](https://github.com/ImL1s/web3-kmp). Please check the new repository for the latest updates.

# kotlin-secure-storage

<p align="center">
  <img src="../docs/images/kmp_crypto_banner.png" alt="kotlin-secure-storage" width="100%">
</p>

<p align="center">
  <a href="#"><img src="https://img.shields.io/badge/kotlin-2.0.21-blue.svg?logo=kotlin" alt="Kotlin"></a>
  <a href="#"><img src="https://img.shields.io/badge/multiplatform-android%20%7C%20ios-brightgreen" alt="Multiplatform"></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/license-Apache%202.0-blue.svg" alt="License"></a>
</p>

<p align="center">
  <strong>🔒 Native secure storage wrapper for Kotlin Multiplatform.</strong>
</p>

<p align="center">
  Securely store sensitive data like private keys and seeds using hardware-backed security modules.
</p>

---

## ✨ Features

| Platform | Implementation | Security |
|----------|----------------|----------|
| **Android** | `EncryptedSharedPreferences` | Android Keystore System (AES-256-GCM) |
| **iOS** | `Keychain Services` | Secure Enclave / Keychain (AES-256) |
| **JVM** | `AES-GCM Encrypted File` | AES-256-GCM (JDK Standard) |

---

## 📦 Installation

```kotlin
// build.gradle.kts
commonMain.dependencies {
    implementation("io.github.iml1s:kotlin-secure-storage:1.0.0")
}
```

---

## 🚀 Usage

```kotlin
// Helper function to get platform storage
val storage = PlatformSecureStorage(context) // context needed on Android

// 1. Store sensitive data
val privateKey = "xprv9s21ZrQH143K..."
storage.put("master_key", privateKey)

// 2. Retrieve data
val savedKey = storage.get("master_key")

// 3. Delete data
storage.delete("master_key")
```

---

## ⚠️ Security Notice

- **Android**: Uses `MasterKey.KeyScheme.AES256_GCM` backed by Android Keystore.
- **iOS**: Uses `kSecClassGenericPassword` with proper access control attributes.
- **JVM (Windows/Desktop)**: Uses **AES-256-GCM** encryption. 
  - Data stored in `~/.kotlin-crypto/secure_storage.dat`.
  - Encryption key auto-generated in `~/.kotlin-crypto/.key` (protected by OS file permissions).
- **Data Cleanup**: Always clear sensitive variables from memory after use when possible.

---

## Support

If this project saved you some time, you can [buy me a coffee](https://buymeacoffee.com/iml1s).
