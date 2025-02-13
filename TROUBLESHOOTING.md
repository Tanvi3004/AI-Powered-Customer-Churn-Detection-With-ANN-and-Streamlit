# --------------------------------------------------------------------------------------------------------
# 🚀 MacOS SSL CERTIFICATE ISSUE & GLOBAL FIX:
# --------------------------------------------------------------------------------------------------------
# If you encounter the following SSL error on macOS when using urllib, TensorFlow datasets, or APIs:
#
# ❌ SSL error: [SSL: CERTIFICATE_VERIFY_FAILED] unable to get local issuer certificate (_ssl.c:1007)
#
# 🔹 **Reason:** Python may not be able to find the correct SSL certificate.
# 🔹 **Fix for macOS Users (Global Solution for All Environments):**
#
# --------------------------------------------------------------------------------------------------------
# 🛠 **STEP 1: Upgrade SSL Certificates (`certifi`)**
# --------------------------------------------------------------------------------------------------------
# First, install or upgrade `certifi`, which provides the latest SSL certificates for Python:
# 
#     ```bash
#     pip install --upgrade certifi
#     ```
#
# --------------------------------------------------------------------------------------------------------
# 🛠 **STEP 2: Verify Where `certifi` Stores SSL Certificates**
# --------------------------------------------------------------------------------------------------------
# Run the following command to find where Python's `certifi` package stores its SSL certificates:
# 
#     ```python
#     import certifi
#     print(certifi.where())  # Should return a valid .pem file path
#     ```
#
# Example output:
# `/opt/anaconda3/lib/python3.12/site-packages/certifi/cacert.pem`
#
# If this returns a valid `.pem` file path, move to the next step.
#
# --------------------------------------------------------------------------------------------------------
# 🛠 **STEP 3: Set the SSL Certificate Path Globally**
# --------------------------------------------------------------------------------------------------------
# To ensure Python always uses the correct SSL certificate, set it permanently in your macOS shell profile:
# 
#     ```bash
#     echo "export SSL_CERT_FILE=$(python -c 'import certifi; print(certifi.where())')" >> ~/.zshrc
#     source ~/.zshrc
#     ```
#
# If using **Bash (instead of Zsh)**, modify `~/.bashrc` instead:
# 
#     ```bash
#     echo "export SSL_CERT_FILE=$(python -c 'import certifi; print(certifi.where())')" >> ~/.bashrc
#     source ~/.bashrc
#     ```
#
# --------------------------------------------------------------------------------------------------------
# 🛠 **STEP 4: Restart Terminal and Verify SSL Configuration**
# --------------------------------------------------------------------------------------------------------
# Close and reopen your terminal, then check if Python is now using the correct SSL settings:
# 
#     ```python
#     import ssl
#     print(ssl.get_default_verify_paths())
#     ```
#
# Expected output should now show:
# `cafile='/opt/anaconda3/lib/python3.12/site-packages/certifi/cacert.pem'`
#
# --------------------------------------------------------------------------------------------------------
# 🛠 **STEP 5: Fix SSL Issues in Conda (If Using Conda)**
# --------------------------------------------------------------------------------------------------------
# If you are using **Anaconda or Miniconda**, reinstall OpenSSL inside Conda:
# 
#     ```bash
#     conda install --force-reinstall -c anaconda openssl
#     ```
#
# Then restart your terminal to apply the changes.
#
# --------------------------------------------------------------------------------------------------------
# 🛠 **STEP 6: Test SSL Connection**
# --------------------------------------------------------------------------------------------------------
# Now, test if Python can securely connect to HTTPS sites:
# 
#     ```python
#     import ssl
#     import urllib.request
# 
#     try:
#         urllib.request.urlopen("https://www.google.com")
#         print("✅ SSL connection successful!")
#     except Exception as e:
#         print("❌ SSL error:", e)
#     ```
#
# Expected output:
# `✅ SSL connection successful!`
#
# --------------------------------------------------------------------------------------------------------
# 🛠 **STEP 7: Test TensorFlow Dataset Download**
# --------------------------------------------------------------------------------------------------------
# If you are using TensorFlow datasets (e.g., IMDB dataset), check if it downloads successfully:
#
#     ```python
#     from tensorflow.keras.datasets import imdb
# 
#     max_features = 10000
#     (X_train, y_train), (X_test, y_test) = imdb.load_data(num_words=max_features)
# 
#     print(f"Training data shape: {X_train.shape}, Training labels shape: {y_train.shape}")
#     print(f"Testing data shape: {X_test.shape}, Testing labels shape: {y_test.shape}")
#     ```
#
# If this runs **without SSL errors**, your **Python, Conda, and global SSL settings are fully fixed!** 🚀  
#
# --------------------------------------------------------------------------------------------------------
# 🎯 **FINAL SUMMARY**
# --------------------------------------------------------------------------------------------------------
# ✅ Upgraded `certifi` to get the latest SSL certificates  
# ✅ Set SSL certificate path globally in `~/.zshrc` for all Python environments  
# ✅ Verified Python is using the correct `certifi` path  
# ✅ Reinstalled OpenSSL in Conda for compatibility  
# ✅ Tested global SSL functionality with Python and TensorFlow  
#
# 🚀 **Your Mac is now permanently configured to avoid SSL errors!** 🚀
# --------------------------------------------------------------------------------------------------------
