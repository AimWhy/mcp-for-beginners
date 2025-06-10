<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "2aa9dbc165e104764fa57e8a0d3f1c73",
  "translation_date": "2025-06-10T05:17:18+00:00",
  "source_file": "10-StreamliningAIWorkflowsBuildingAnMCPServerWithAIToolkit/lab1/README.md",
  "language_code": "pa"
}
-->
# 🚀 ਮੋਡੀਊਲ 1: AI ਟੂਲਕਿਟ ਬੁਨਿਆਦੀ ਜਾਣਕਾਰੀਆਂ

[![Duration](https://img.shields.io/badge/Duration-15%20minutes-blue.svg)]()
[![Difficulty](https://img.shields.io/badge/Difficulty-Beginner-green.svg)]()
[![Prerequisites](https://img.shields.io/badge/Prerequisites-VS%20Code-orange.svg)]()

## 📋 ਸਿੱਖਣ ਦੇ ਮਕਸਦ

ਇਸ ਮੋਡੀਊਲ ਦੇ ਅੰਤ ਤੱਕ, ਤੁਸੀਂ ਸਮਰੱਥ ਹੋਵੋਗੇ:
- ✅ Visual Studio Code ਲਈ AI Toolkit ਨੂੰ ਇੰਸਟਾਲ ਅਤੇ ਸੰਰਚਿਤ ਕਰਨਾ
- ✅ Model Catalog ਵਿਚ ਨੈਵੀਗੇਟ ਕਰਨਾ ਅਤੇ ਵੱਖ-ਵੱਖ ਮਾਡਲ ਸਰੋਤਾਂ ਨੂੰ ਸਮਝਣਾ
- ✅ ਮਾਡਲ ਟੈਸਟਿੰਗ ਅਤੇ ਪ੍ਰਯੋਗ ਲਈ Playground ਦੀ ਵਰਤੋਂ ਕਰਨਾ
- ✅ Agent Builder ਦੀ ਵਰਤੋਂ ਨਾਲ ਕਸਟਮ AI ਏਜੰਟ ਬਣਾਉਣਾ
- ✅ ਵੱਖ-ਵੱਖ ਪ੍ਰਦਾਤਾਵਾਂ ਦੇ ਮਾਡਲ ਪ੍ਰਦਰਸ਼ਨ ਦੀ ਤੁਲਨਾ ਕਰਨਾ
- ✅ ਪ੍ਰੋੰਪਟ ਇੰਜੀਨੀਅਰਿੰਗ ਲਈ ਸਭ ਤੋਂ ਵਧੀਆ ਅਭਿਆਸ ਲਾਗੂ ਕਰਨਾ

## 🧠 AI Toolkit (AITK) ਦਾ ਪਰਿਚਯ

**Visual Studio Code ਲਈ AI Toolkit** ਮਾਈਕਰੋਸਾਫਟ ਦਾ ਪ੍ਰਮੁੱਖ ਐਕਸਟੈਂਸ਼ਨ ਹੈ ਜੋ VS Code ਨੂੰ ਇੱਕ ਪੂਰਨ AI ਵਿਕਾਸ ਮਾਹੌਲ ਵਿੱਚ ਬਦਲ ਦਿੰਦਾ ਹੈ। ਇਹ AI ਖੋਜ ਅਤੇ ਪ੍ਰਯੋਗਿਕ ਐਪਲੀਕੇਸ਼ਨ ਵਿਕਾਸ ਦੇ ਵਿਚਕਾਰ ਕੜੀ ਬਣਾਉਂਦਾ ਹੈ, ਜਿਸ ਨਾਲ ਜਨਰੇਟਿਵ AI ਹਰ ਤਰ੍ਹਾਂ ਦੇ ਡਿਵੈਲਪਰਾਂ ਲਈ ਆਸਾਨ ਹੋ ਜਾਂਦਾ ਹੈ।

### 🌟 ਮੁੱਖ ਖੂਬੀਆਂ

| ਫੀਚਰ | ਵੇਰਵਾ | ਵਰਤੋਂ ਦਾ ਮਾਮਲਾ |
|---------|-------------|----------|
| **🗂️ Model Catalog** | GitHub, ONNX, OpenAI, Anthropic, Google ਤੋਂ 100+ ਮਾਡਲਾਂ ਤੱਕ ਪਹੁੰਚ | ਮਾਡਲ ਖੋਜ ਅਤੇ ਚੋਣ |
| **🔌 BYOM Support** | ਆਪਣੇ ਮਾਡਲ (ਲੋਕਲ/ਰਿਮੋਟ) ਨੂੰ ਜੋੜੋ | ਕਸਟਮ ਮਾਡਲ ਡਿਪਲੋਇਮੈਂਟ |
| **🎮 ਇੰਟਰਐਕਟਿਵ Playground** | ਚੈਟ ਇੰਟਰਫੇਸ ਨਾਲ ਰੀਅਲ-ਟਾਈਮ ਮਾਡਲ ਟੈਸਟਿੰਗ | ਤੇਜ਼ ਪ੍ਰੋਟੋਟਾਈਪਿੰਗ ਅਤੇ ਟੈਸਟਿੰਗ |
| **📎 ਮਲਟੀ-ਮੋਡਲ ਸਹਾਇਤਾ** | ਟੈਕਸਟ, ਚਿੱਤਰ ਅਤੇ ਅਟੈਚਮੈਂਟ ਸੰਭਾਲੋ | ਜਟਿਲ AI ਐਪਲੀਕੇਸ਼ਨ |
| **⚡ ਬੈਚ ਪ੍ਰੋਸੈਸਿੰਗ** | ਇਕੱਠੇ ਕਈ ਪ੍ਰੋੰਪਟ ਚਲਾਓ | ਪ੍ਰਭਾਵਸ਼ਾਲੀ ਟੈਸਟਿੰਗ ਵਰਕਫਲੋਜ਼ |
| **📊 ਮਾਡਲ ਮੁਲਾਂਕਣ** | ਇੰਬਿਲਟ ਮੈਟਰਿਕਸ (F1, ਸਬੰਧਿਤਤਾ, ਸਮਾਨਤਾ, ਸੰਗਤੀ) | ਪ੍ਰਦਰਸ਼ਨ ਮੁਲਾਂਕਣ |

### 🎯 AI Toolkit ਕਿਉਂ ਮਹੱਤਵਪੂਰਨ ਹੈ

- **🚀 ਤੇਜ਼ ਵਿਕਾਸ**: ਵਿਚਾਰ ਤੋਂ ਪ੍ਰੋਟੋਟਾਈਪ ਤੱਕ ਕੁਝ ਮਿੰਟਾਂ ਵਿੱਚ
- **🔄 ਇਕਠਾ ਵਰਕਫਲੋ**: ਕਈ AI ਪ੍ਰਦਾਤਾਵਾਂ ਲਈ ਇੱਕ ਇੰਟਰਫੇਸ
- **🧪 ਆਸਾਨ ਪ੍ਰਯੋਗ**: ਬਿਨਾਂ ਜਟਿਲ ਸੈਟਅੱਪ ਦੇ ਮਾਡਲਾਂ ਦੀ ਤੁਲਨਾ ਕਰੋ
- **📈 ਪ੍ਰੋਡਕਸ਼ਨ ਤਿਆਰ**: ਪ੍ਰੋਟੋਟਾਈਪ ਤੋਂ ਡਿਪਲੋਇਮੈਂਟ ਤੱਕ ਬਿਨਾਂ ਰੁਕਾਵਟ

## 🛠️ ਲੋੜੀਂਦੇ ਤੱਤ ਅਤੇ ਸੈਟਅੱਪ

### 📦 AI Toolkit ਐਕਸਟੈਂਸ਼ਨ ਇੰਸਟਾਲ ਕਰੋ

**ਕਦਮ 1: ਐਕਸਟੈਂਸ਼ਨ ਮਾਰਕੀਟਪਲੇਸ ਤੱਕ ਪਹੁੰਚੋ**
1. Visual Studio Code ਖੋਲ੍ਹੋ
2. Extensions ਵਿਊ ਤੇ ਜਾਓ (`Ctrl+Shift+X` ਜਾਂ `Cmd+Shift+X`)
3. "AI Toolkit" ਖੋਜੋ

**ਕਦਮ 2: ਆਪਣਾ ਵਰਜਨ ਚੁਣੋ**
- **🟢 ਰਿਲੀਜ਼**: ਉਤਪਾਦਨ ਵਰਤੋਂ ਲਈ ਸਿਫਾਰਸ਼ੀ
- **🔶 ਪ੍ਰੀ-ਰਿਲੀਜ਼**: ਨਵੇਂ ਫੀਚਰਾਂ ਲਈ ਪਹਿਲਾਂ ਪਹੁੰਚ

**ਕਦਮ 3: ਇੰਸਟਾਲ ਅਤੇ ਐਕਟੀਵੇਟ ਕਰੋ**

![AI Toolkit Extension](../../../../translated_images/aitkext.d28945a03eed003c39fc39bc96ae655af9b64b9b922e78e88b07214420ed7985.pa.png)

### ✅ ਜਾਂਚ ਸੂਚੀ
- [ ] AI Toolkit ਆਈਕਨ VS Code ਸਾਈਡਬਾਰ ਵਿੱਚ ਦਿਖਾਈ ਦੇ ਰਿਹਾ ਹੈ
- [ ] ਐਕਸਟੈਂਸ਼ਨ ਚਾਲੂ ਅਤੇ ਐਕਟੀਵੇਟ ਹੈ
- [ ] ਆਉਟਪੁੱਟ ਪੈਨਲ ਵਿੱਚ ਕੋਈ ਇੰਸਟਾਲੇਸ਼ਨ ਗਲਤੀ ਨਹੀਂ

## 🧪 ਹੱਥ-ਵਰਕ ਅਭਿਆਸ 1: GitHub ਮਾਡਲਾਂ ਦੀ ਖੋਜ

**🎯 ਮਕਸਦ**: Model Catalog ਨੂੰ ਸਮਝੋ ਅਤੇ ਆਪਣਾ ਪਹਿਲਾ AI ਮਾਡਲ ਟੈਸਟ ਕਰੋ

### 📊 ਕਦਮ 1: Model Catalog ਵਿੱਚ ਨੈਵੀਗੇਟ ਕਰੋ

Model Catalog ਤੁਹਾਡੇ ਲਈ AI ਪਰਿਵਾਰ ਦਾ ਦਰਵਾਜ਼ਾ ਹੈ। ਇਹ ਕਈ ਪ੍ਰਦਾਤਾਵਾਂ ਤੋਂ ਮਾਡਲ ਇਕੱਠੇ ਕਰਦਾ ਹੈ, ਜਿਸ ਨਾਲ ਵਿਕਲਪਾਂ ਦੀ ਖੋਜ ਅਤੇ ਤੁਲਨਾ ਆਸਾਨ ਹੋ ਜਾਂਦੀ ਹੈ।

**🔍 ਨੈਵੀਗੇਸ਼ਨ ਗਾਈਡ:**

AI Toolkit ਸਾਈਡਬਾਰ ਵਿੱਚ **MODELS - Catalog** 'ਤੇ ਕਲਿੱਕ ਕਰੋ

![Model Catalog](../../../../translated_images/aimodel.263ed2be013d8fb0e2265c4f742cfe490f6f00eca5e132ec50438c8e826e34ed.pa.png)

**💡 ਪ੍ਰੋ ਟਿਪ**: ਆਪਣੇ ਵਰਤੋਂ ਦੇ ਮਾਮਲੇ ਨਾਲ ਮੇਲ ਖਾਂਦੇ ਖਾਸ ਖੂਬੀਆਂ ਵਾਲੇ ਮਾਡਲ ਲੱਭੋ (ਜਿਵੇਂ ਕੋਡ ਜਨਰੇਸ਼ਨ, ਰਚਨਾਤਮਕ ਲਿਖਾਈ, ਵਿਸ਼ਲੇਸ਼ਣ)।

**⚠️ ਨੋਟ**: GitHub-ਹੋਸਟ ਕੀਤੇ ਮਾਡਲ (ਜਿਵੇਂ GitHub Models) ਮੁਫ਼ਤ ਹਨ ਪਰ ਰਿਕਵੇਸਟ ਅਤੇ ਟੋਕਨ ਦੀਆਂ ਸੀਮਾਵਾਂ ਦੇ ਅਧੀਨ ਹਨ। ਜੇ ਤੁਸੀਂ GitHub ਤੋਂ ਬਾਹਰ ਦੇ ਮਾਡਲਾਂ (ਜਿਵੇਂ Azure AI ਜਾਂ ਹੋਰ ਐਂਡਪੌਇੰਟਸ ਵਾਲੇ) ਤੱਕ ਪਹੁੰਚਣਾ ਚਾਹੁੰਦੇ ਹੋ, ਤਾਂ ਤੁਹਾਨੂੰ ਸਹੀ API ਕੁੰਜੀ ਜਾਂ ਪ੍ਰਮਾਣਿਕਤਾ ਦੇਣੀ ਪਵੇਗੀ।

### 🚀 ਕਦਮ 2: ਆਪਣਾ ਪਹਿਲਾ ਮਾਡਲ ਸ਼ਾਮਿਲ ਕਰੋ ਅਤੇ ਸੰਰਚਿਤ ਕਰੋ

**ਮਾਡਲ ਚੋਣ ਰਣਨੀਤੀ:**
- **GPT-4.1**: ਜਟਿਲ ਤਰਕ ਅਤੇ ਵਿਸ਼ਲੇਸ਼ਣ ਲਈ ਬਿਹਤਰ
- **Phi-4-mini**: ਸਧਾਰਣ ਕੰਮਾਂ ਲਈ ਹਲਕਾ ਅਤੇ ਤੇਜ਼ ਜਵਾਬ

**🔧 ਸੰਰਚਨਾ ਪ੍ਰਕਿਰਿਆ:**
1. ਕੈਟਾਲੌਗ ਵਿੱਚੋਂ **OpenAI GPT-4.1** ਚੁਣੋ
2. **Add to My Models** 'ਤੇ ਕਲਿੱਕ ਕਰੋ - ਇਸ ਨਾਲ ਮਾਡਲ ਵਰਤੋਂ ਲਈ ਦਰਜ ਹੋ ਜਾਵੇਗਾ
3. **Try in Playground** ਚੁਣੋ ਤਾਂ ਜੋ ਟੈਸਟਿੰਗ ਮਾਹੌਲ ਖੁਲ ਜਾਵੇ
4. ਮਾਡਲ ਦੀ ਸ਼ੁਰੂਆਤ ਦੀ ਉਡੀਕ ਕਰੋ (ਪਹਿਲੀ ਵਾਰੀ ਸੈਟਅੱਪ ਵਿੱਚ ਕੁਝ ਸਮਾਂ ਲੱਗ ਸਕਦਾ ਹੈ)

![Playground Setup](../../../../translated_images/playground.dd6f5141344878ca4d4f3de819775da7b113518941accf37c291117c602f85db.pa.png)

**⚙️ ਮਾਡਲ ਪੈਰਾਮੀਟਰਾਂ ਨੂੰ ਸਮਝਣਾ:**
- **Temperature**: ਰਚਨਾਤਮਕਤਾ ਨੂੰ ਨਿਯੰਤਰਿਤ ਕਰਦਾ ਹੈ (0 = ਨਿਰਧਾਰਿਤ, 1 = ਰਚਨਾਤਮਕ)
- **Max Tokens**: ਜਵਾਬ ਦੀ ਵੱਧ ਤੋਂ ਵੱਧ ਲੰਬਾਈ
- **Top-p**: ਜਵਾਬ ਵਿੱਚ ਵੱਖ-ਵੱਖਤਾ ਲਈ ਨਿਊਕਲੀਅਸ ਸੈਂਪਲਿੰਗ

### 🎯 ਕਦਮ 3: Playground ਇੰਟਰਫੇਸ 'ਤੇ ਕਾਬੂ ਪਾਓ

Playground ਤੁਹਾਡੀ AI ਪ੍ਰਯੋਗਸ਼ਾਲਾ ਹੈ। ਇਸਦੀ ਪੂਰੀ ਸਮਰੱਥਾ ਵਰਤਣ ਲਈ:

**🎨 ਪ੍ਰੋੰਪਟ ਇੰਜੀਨੀਅਰਿੰਗ ਲਈ ਸਭ ਤੋਂ ਵਧੀਆ ਅਭਿਆਸ:**
1. **ਸਪਸ਼ਟ ਰਹੋ**: ਸਾਫ਼ ਅਤੇ ਵਿਸਥਾਰਪੂਰਕ ਹੁਕਮ ਚੰਗੇ ਨਤੀਜੇ ਦਿੰਦੇ ਹਨ
2. **ਸੰਦਰਭ ਦਿਓ**: ਸੰਬੰਧਿਤ ਪਿਛੋਕੜ ਜਾਣਕਾਰੀ ਸ਼ਾਮਿਲ ਕਰੋ
3. **ਉਦਾਹਰਣਾਂ ਵਰਤੋ**: ਮਾਡਲ ਨੂੰ ਦਿਖਾਓ ਕਿ ਤੁਸੀਂ ਕੀ ਚਾਹੁੰਦੇ ਹੋ
4. **ਦੁਹਰਾਓ**: ਸ਼ੁਰੂਆਤੀ ਨਤੀਜਿਆਂ ਦੇ ਆਧਾਰ 'ਤੇ ਪ੍ਰੋੰਪਟ ਸੁਧਾਰੋ

**🧪 ਟੈਸਟਿੰਗ ਸਿਨਾਰਿਓਜ਼:**
```markdown
# Example 1: Code Generation
"Write a Python function that calculates the factorial of a number using recursion. Include error handling and docstrings."

# Example 2: Creative Writing
"Write a professional email to a client explaining a project delay, maintaining a positive tone while being transparent about challenges."

# Example 3: Data Analysis
"Analyze this sales data and provide insights: [paste your data]. Focus on trends, anomalies, and actionable recommendations."
```

![Testing Results](../../../../translated_images/result.1dfcf211fb359cf65902b09db191d3bfc65713ca15e279c1a30be213bb526949.pa.png)

### 🏆 ਚੈਲੈਂਜ ਅਭਿਆਸ: ਮਾਡਲ ਪ੍ਰਦਰਸ਼ਨ ਦੀ ਤੁਲਨਾ

**🎯 ਮਕਸਦ**: ਇਕੋ ਜਿਹੇ ਪ੍ਰੋੰਪਟ ਨਾਲ ਵੱਖ-ਵੱਖ ਮਾਡਲਾਂ ਦੀ ਤੁਲਨਾ ਕਰਕੇ ਉਹਨਾਂ ਦੀਆਂ ਖੂਬੀਆਂ ਸਮਝੋ

**📋 ਹਦਾਇਤਾਂ:**
1. ਆਪਣੀ ਵਰਕਸਪੇਸ ਵਿੱਚ **Phi-4-mini** ਸ਼ਾਮਿਲ ਕਰੋ
2. GPT-4.1 ਅਤੇ Phi-4-mini ਦੋਹਾਂ ਲਈ ਇਕੋ ਪ੍ਰੋੰਪਟ ਵਰਤੋ

![set](../../../../translated_images/set.88132df189ecde2cbbda256c1841db5aac8e9bdeba1a4e343dfa031b9545d6c9.pa.png)

3. ਜਵਾਬ ਦੀ ਗੁਣਵੱਤਾ, ਗਤੀ ਅਤੇ ਸਹੀਤਾ ਦੀ ਤੁਲਨਾ ਕਰੋ
4. ਨਤੀਜੇ ਸੈਕਸ਼ਨ ਵਿੱਚ ਆਪਣੀਆਂ ਖੋਜਾਂ ਦਰਜ ਕਰੋ

![Model Comparison](../../../../translated_images/compare.97746cd0f907495503c1fc217739f3890dc76ea5f6fd92379a6db0cc331feb58.pa.png)

**💡 ਮੁੱਖ ਜਾਣਕਾਰੀਆਂ ਜੋ ਤੁਸੀਂ ਲੱਭੋਗੇ:**
- ਕਦੋਂ LLM ਅਤੇ ਕਦੋਂ SLM ਵਰਤਣਾ ਹੈ
- ਲਾਗਤ ਅਤੇ ਪ੍ਰਦਰਸ਼ਨ ਵਿਚਕਾਰ ਤਰਜੀਹ
- ਵੱਖ-ਵੱਖ ਮਾਡਲਾਂ ਦੀ ਵਿਸ਼ੇਸ਼ ਖੂਬੀਆਂ

## 🤖 ਹੱਥ-ਵਰਕ ਅਭਿਆਸ 2: Agent Builder ਨਾਲ ਕਸਟਮ ਏਜੰਟ ਬਣਾਉਣਾ

**🎯 ਮਕਸਦ**: ਖਾਸ ਕੰਮਾਂ ਅਤੇ ਵਰਕਫਲੋਜ਼ ਲਈ ਵਿਸ਼ੇਸ਼ AI ਏਜੰਟ ਬਣਾਉਣਾ

### 🏗️ ਕਦਮ 1: Agent Builder ਨੂੰ ਸਮਝਣਾ

Agent Builder AI Toolkit ਦੀ ਸਭ ਤੋਂ ਖਾਸ ਖੂਬੀ ਹੈ। ਇਹ ਤੁਹਾਨੂੰ ਵੱਡੇ ਭਾਸ਼ਾ ਮਾਡਲਾਂ ਦੀ ਤਾਕਤ ਨੂੰ ਕਸਟਮ ਹੁਕਮਾਂ, ਖਾਸ ਪੈਰਾਮੀਟਰਾਂ ਅਤੇ ਵਿਸ਼ੇਸ਼ ਗਿਆਨ ਨਾਲ ਮਿਲਾ ਕੇ ਨਿਸ਼ਾਨਾ-ਨਿਰਧਾਰਤ AI ਸਹਾਇਕ ਬਣਾਉਣ ਦੀ ਆਜ਼ਾਦੀ ਦਿੰਦਾ ਹੈ।

**🧠 Agent ਦੀ ਬਣਤਰ ਦੇ ਹਿੱਸੇ:**
- **ਮੂਲ ਮਾਡਲ**: ਬੁਨਿਆਦੀ LLM (GPT-4, Groks, Phi ਆਦਿ)
- **ਸਿਸਟਮ ਪ੍ਰੋੰਪਟ**: ਏਜੰਟ ਦੀ ਸ਼ਖਸੀਅਤ ਅਤੇ ਵਿਹਾਰ ਨੂੰ ਪਰਿਭਾਸ਼ਿਤ ਕਰਦਾ ਹੈ
- **ਪੈਰਾਮੀਟਰ**: ਵਧੀਆ ਪ੍ਰਦਰਸ਼ਨ ਲਈ ਸੁਧਾਰੇ ਹੋਏ ਸੈਟਿੰਗਜ਼
- **ਟੂਲਜ਼ ਇੰਟੀਗ੍ਰੇਸ਼ਨ**: ਬਾਹਰੀ APIs ਅਤੇ MCP ਸਰਵਿਸਜ਼ ਨਾਲ ਜੁੜਾਈ
- **ਮੇਮੋਰੀ**: ਗੱਲਬਾਤ ਦਾ ਸੰਦਰਭ ਅਤੇ ਸੈਸ਼ਨ ਪੈਰਸਿਸਟੈਂਸ

![Agent Builder Interface](../../../../translated_images/agentbuilder.25895b2d2f8c02e7aa99dd40e105877a6f1db8f0441180087e39db67744b361f.pa.png)

### ⚙️ ਕਦਮ 2: Agent ਸੰਰਚਨਾ ਦਾ ਵਿਸਤਾਰ

**🎨 ਪ੍ਰਭਾਵਸ਼ਾਲੀ ਸਿਸਟਮ ਪ੍ਰੋੰਪਟ ਬਣਾਉਣਾ:**
```markdown
# Template Structure:
## Role Definition
You are a [specific role] with expertise in [domain].

## Capabilities
- List specific abilities
- Define scope of knowledge
- Clarify limitations

## Behavior Guidelines
- Response style (formal, casual, technical)
- Output format preferences
- Error handling approach

## Examples
Provide 2-3 examples of ideal interactions
```

*ਤੁਸੀਂ Generate System Prompt ਦੀ ਵਰਤੋਂ ਕਰਕੇ AI ਦੀ ਮਦਦ ਨਾਲ ਪ੍ਰੋੰਪਟ ਬਣਾਉਣ ਅਤੇ ਸੁਧਾਰਨ ਵੀ ਕਰ ਸਕਦੇ ਹੋ*

**🔧 ਪੈਰਾਮੀਟਰ ਅਪਟੀਮਾਈਜ਼ੇਸ਼ਨ:**
| ਪੈਰਾਮੀਟਰ | ਸਿਫਾਰਸ਼ੀਦਾ ਰੇਂਜ | ਵਰਤੋਂ ਦਾ ਮਾਮਲਾ |
|-----------|------------------|----------|
| **Temperature** | 0.1-0.3 | ਤਕਨੀਕੀ/ਤੱਥਾਂ ਵਾਲੇ ਜਵਾਬ |
| **Temperature** | 0.7-0.9 | ਰਚਨਾਤਮਕ/ਵਿਚਾਰ-ਵਟਾਂਦਰਾ ਕੰਮ |
| **Max Tokens** | 500-1000 | ਸੰਖੇਪ ਜਵਾਬ |
| **Max Tokens** | 2000-4000 | ਵਿਸਥਾਰਪੂਰਕ ਵਿਆਖਿਆਵਾਂ |

### 🐍 ਕਦਮ 3: ਪ੍ਰਯੋਗਾਤਮਕ ਅਭਿਆਸ - Python ਪ੍ਰੋਗ੍ਰਾਮਿੰਗ ਏਜੰਟ

**🎯 ਮਿਸ਼ਨ**: ਇੱਕ ਵਿਸ਼ੇਸ਼ Python ਕੋਡਿੰਗ ਸਹਾਇਕ ਬਣਾਉਣਾ

**📋 ਸੰਰਚਨਾ ਕਦਮ:**

1. **ਮਾਡਲ ਚੋਣ**: **Claude 3.5 Sonnet** ਚੁਣੋ (ਕੋਡ ਲਈ ਸ਼ਾਨਦਾਰ)

2. **ਸਿਸਟਮ ਪ੍ਰੋੰਪਟ ਡਿਜ਼ਾਈਨ**:
```markdown
# Python Programming Expert Agent

## Role
You are a senior Python developer with 10+ years of experience. You excel at writing clean, efficient, and well-documented Python code.

## Capabilities
- Write production-ready Python code
- Debug complex issues
- Explain code concepts clearly
- Suggest best practices and optimizations
- Provide complete working examples

## Response Format
- Always include docstrings
- Add inline comments for complex logic
- Suggest testing approaches
- Mention relevant libraries when applicable

## Code Quality Standards
- Follow PEP 8 style guidelines
- Use type hints where appropriate
- Handle exceptions gracefully
- Write readable, maintainable code
```

3. **ਪੈਰਾਮੀਟਰ ਸੰਰਚਨਾ**:
   - Temperature: 0.2 (ਸਥਿਰ, ਭਰੋਸੇਮੰਦ ਕੋਡ ਲਈ)
   - Max Tokens: 2000 (ਵਿਸਥਾਰਪੂਰਕ ਵਿਆਖਿਆਵਾਂ)
   - Top-p: 0.9 (ਸੰਤੁਲਿਤ ਰਚਨਾਤਮਕਤਾ)

![Python Agent Configuration](../../../../translated_images/pythonagent.5e51b406401c165fcabfd66f2d943c27f46b5fed0f9fb73abefc9e91ca3489d4.pa.png)

### 🧪 ਕਦਮ 4: ਆਪਣਾ Python ਏਜੰਟ ਟੈਸਟ ਕਰੋ

**ਟੈਸਟ ਸਿਨਾਰਿਓਜ਼:**
1. **ਮੂਲ ਫੰਕਸ਼ਨ**: "Prime numbers ਲੱਭਣ ਲਈ ਫੰਕਸ਼ਨ ਬਣਾਓ"
2. **ਜਟਿਲ ਅਲਗੋਰਿਦਮ**: "Binary search tree ਬਣਾਓ ਜਿਸ ਵਿੱਚ insert, delete ਅਤੇ search ਮੈਥਡ ਹੋਣ"
3. **ਅਸਲੀ ਦੁਨੀਆ ਸਮੱਸਿਆ**: "ਇੱਕ ਵੈੱਬ ਸਕ੍ਰੈਪਰ ਬਣਾਓ ਜੋ rate limiting ਅਤੇ retries ਨੂੰ ਸੰਭਾਲਦਾ ਹੈ"
4. **ਡਿਬੱਗਿੰਗ**: "ਇਸ ਕੋਡ ਨੂੰ ਠੀਕ ਕਰੋ [buggy code ਪੇਸਟ ਕਰੋ]"

**🏆 ਸਫਲਤਾ ਦੇ ਮਾਪਦੰਡ:**
- ✅ ਕੋਡ ਬਿਨਾਂ ਗਲਤੀਆਂ ਚੱਲਦਾ ਹੈ
- ✅ ਢੰਗ ਨਾਲ ਦਸਤਾਵੇਜ਼ੀਕਰਨ ਹੈ
- ✅ Python ਦੇ ਸਭ ਤੋਂ ਵਧੀਆ ਅਭਿਆਸਾਂ ਦੀ ਪਾਲਣਾ ਕਰਦਾ ਹੈ
- ✅ ਸਪਸ਼ਟ ਵਿਆਖਿਆਵਾਂ ਦਿੰਦਾ ਹੈ
- ✅ ਸੁਧਾਰ ਸੁਝਾਅ ਦਿੰਦਾ ਹੈ

## 🎓 ਮੋਡੀਊਲ 1 ਸੰਖੇਪ ਅਤੇ ਅਗਲੇ ਕਦਮ

### 📊 ਗਿਆਨ ਦੀ ਜਾਂਚ

ਆਪਣੀ ਸਮਝ ਦਾ ਟੈਸਟ ਲਓ:
- [ ] ਕੀ ਤੁਸੀਂ ਕੈਟਾਲੌਗ ਵਿੱਚ ਮਾਡਲਾਂ ਦੇ ਫਰਕ ਨੂੰ ਸਮਝਾ ਸਕਦੇ ਹੋ?
- [ ] ਕੀ ਤੁਸੀਂ ਕਸਟਮ ਏਜੰਟ ਬਣਾਇਆ ਅਤੇ ਟੈਸਟ ਕੀਤਾ ਹੈ?
- [ ] ਕੀ ਤੁਸੀਂ ਵੱਖ-ਵੱਖ ਵਰਤੋਂ ਦੇ ਮਾਮਲਿਆਂ ਲਈ ਪੈਰਾਮੀਟਰਾਂ ਨੂੰ ਸੁਧਾਰਨਾ ਸਮਝਦੇ ਹੋ?
- [ ] ਕੀ ਤੁਸੀਂ ਪ੍ਰਭਾਵਸ਼ਾਲੀ ਸਿਸਟਮ ਪ੍ਰੋੰਪਟ ਡਿਜ਼ਾਈਨ ਕਰ ਸਕਦੇ ਹੋ?

### 📚 ਵਾਧੂ ਸਰੋਤ

- **AI Toolkit ਦਸਤਾਵੇਜ਼**: [Official Microsoft Docs](https://github.com/microsoft/vscode-ai-toolkit)
- **Prompt Engineering Guide**: [Best Practices](https://platform.openai.com/docs/guides/prompt-engineering)
- **AI Toolkit ਵਿੱਚ ਮਾਡਲ**: [Models in Develpment](https://github.com/microsoft/vscode-ai-toolkit/blob/main/doc/models.md)

**🎉 ਵਧਾਈਆਂ!** ਤੁਸੀਂ AI Toolkit ਦੇ ਬੁਨਿਆਦੀ ਸਿਧਾਂਤਾਂ 'ਤੇ ਕਾਬੂ ਪਾ ਲਿਆ ਹੈ ਅਤੇ ਹੋਰ ਅਡਵਾਂਸ AI ਐਪਲੀਕੇਸ਼ਨਾਂ ਬਣਾਉਣ ਲਈ ਤਿਆਰ ਹੋ।

### 🔜 ਅਗਲੇ ਮੋਡੀਊਲ ਵੱਲ ਵਧੋ

ਹੋਰ ਅਡਵਾਂਸ ਖੂਬੀਆਂ ਲਈ ਤਿਆਰ ਹੋ? ਜਾਰੀ ਰੱਖ

**ਅਸਵੀਕਾਰੋक्ति**:  
ਇਹ ਦਸਤਾਵੇਜ਼ AI ਅਨੁਵਾਦ ਸੇਵਾ [Co-op Translator](https://github.com/Azure/co-op-translator) ਦੀ ਵਰਤੋਂ ਕਰਕੇ ਅਨੁਵਾਦ ਕੀਤਾ ਗਿਆ ਹੈ। ਜਦੋਂ ਕਿ ਅਸੀਂ ਸਹੀਤਾ ਲਈ ਕੋਸ਼ਿਸ਼ ਕਰਦੇ ਹਾਂ, ਕਿਰਪਾ ਕਰਕੇ ਧਿਆਨ ਵਿੱਚ ਰੱਖੋ ਕਿ ਆਟੋਮੇਟਿਕ ਅਨੁਵਾਦਾਂ ਵਿੱਚ ਗਲਤੀਆਂ ਜਾਂ ਅਣਸਹੀਤੀਆਂ ਹੋ ਸਕਦੀਆਂ ਹਨ। ਮੂਲ ਦਸਤਾਵੇਜ਼ ਆਪਣੀ ਮੂਲ ਭਾਸ਼ਾ ਵਿੱਚ ਪ੍ਰਮਾਣਿਕ ਸਰੋਤ ਮੰਨਿਆ ਜਾਣਾ ਚਾਹੀਦਾ ਹੈ। ਜਰੂਰੀ ਜਾਣਕਾਰੀ ਲਈ, ਪੇਸ਼ੇਵਰ ਮਨੁੱਖੀ ਅਨੁਵਾਦ ਦੀ ਸਿਫਾਰਸ਼ ਕੀਤੀ ਜਾਂਦੀ ਹੈ। ਇਸ ਅਨੁਵਾਦ ਦੀ ਵਰਤੋਂ ਤੋਂ ਉੱਪਜਣ ਵਾਲੀਆਂ ਕਿਸੇ ਵੀ ਗਲਤਫਹਮੀਆਂ ਜਾਂ ਗਲਤ ਵਿਆਖਿਆਵਾਂ ਲਈ ਅਸੀਂ ਜ਼ਿੰਮੇਵਾਰ ਨਹੀਂ ਹਾਂ।