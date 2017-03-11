---
title: "/keycontainer (C# Compiler Options) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "/keycontainer"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/keycontainer compiler option [C#]"
  - "keycontainer compiler option [C#]"
  - "-keycontainer compiler option [C#]"
ms.assetid: b3982b6d-2382-4f7e-bebd-ce98eaa30763
caps.latest.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 17
---
# /keycontainer (C# Compiler Options)
暗号化キー コンテナーの名前を指定します。  
  
## 構文  
  
```  
/keycontainer:string  
```  
  
## Arguments  
 `string`  
 厳密名キーのコンテナー名。  
  
## 解説  
 **\/keycontainer** オプションが指定された場合、コンパイラは、指定されたコンテナーに格納された公開キーをアセンブリ マニフェストに追加し、最終的なアセンブリを秘密キーで署名することによって、共有可能なコンポーネントを生成します。  キー ファイルを生成するには、コマンド ラインで" sn \- k `file` "と入力します。sn \- i、キー ペアがコンテナーにインストールされます。  
  
 [\/target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md) を使用してコンパイルすると、キー ファイル名はモジュールに保持され、[\/addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md) を使用してこのモジュールをコンパイルするときに作成されるアセンブリに組み込まれます。  
  
 このオプションは、任意の Microsoft Intermediate Language \(MSIL\) モジュールのソース コードで、カスタム属性 \(<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName>\) として指定することもできます。  
  
 [\/keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md) を使用して、暗号に関する情報をコンパイラに渡すこともできます。  公開キーのみアセンブリ マニフェストに追加しておき、アセンブリへの署名については、テストが終わるまで保留にする場合は、[\/delaysign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md) を使用します。  
  
 詳細については、「[厳密な名前付きアセンブリの作成と使用](../Topic/Creating%20and%20Using%20Strong-Named%20Assemblies.md)」および「[アセンブリへの遅延署名](../Topic/Delay%20Signing%20an%20Assembly.md)」を参照してください。  
  
### Visual Studio 開発環境でこのコンパイラ オプションを設定するには  
  
1.  このコンパイラ オプションは、Visual Studio 開発環境では使用できません。  
  
 このコンパイラ オプションには、<xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A> を使用してプログラムでアクセスできます。  
  
## 参照  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [方法 : プロジェクト プロパティおよび構成設定を変更する](http://msdn.microsoft.com/ja-jp/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)