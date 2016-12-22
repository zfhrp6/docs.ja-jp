---
title: "/bugreport (C# Compiler Options) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/bugreport"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/bugreport compiler option [C#]"
  - "-bugreport compiler option [C#]"
  - "bugreport compiler option [C#]"
ms.assetid: f39665e3-4f6f-4357-88a2-3274c7bec0c1
caps.latest.revision: 20
caps.handback.revision: 20
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /bugreport (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

後で分析を行うことができるように、デバッグ情報をファイルに出力するように指定します。  
  
## 構文  
  
```  
/bugreport:file  
```  
  
## Arguments  
 `file`  
 バグ レポートを作成するファイルの名前。  
  
## 解説  
 **\/bugreport** オプションを指定すると、`file` には次の情報が出力されます。  
  
-   コンパイル時のすべてのソース コード ファイルのコピー。  
  
-   コンパイルで使用されたコンパイラ オプションの一覧。  
  
-   コンパイラ、ランタイム、およびオペレーティング システムのバージョン情報。  
  
-   .NET Framework \(SDK を含む\) に付属のアセンブリを除く参照アセンブリおよびモジュール \(16 進数として保存\)。  
  
-   コンパイラの出力 \(指定されている場合\)。  
  
-   問題点の説明。プロンプトが表示されます。  
  
-   問題点の修正方法の説明。プロンプトが表示されます。  
  
 このオプションに **\/errorreport:prompt** または **\/errorreport:send** を指定すると、ファイルに保存される情報が Microsoft Corporation に送信されます。  
  
 すべてのソース コード ファイルのコピーが `file` に組み込まれてしまうため、問題があると思われるコードをできるだけ小さなプログラムとして再生成することがあります。  
  
 このコンパイラ オプションは、Visual Studio で利用できず、プログラムで変更することもできません。  
  
 生成されたファイルの内容により、ソース コードが公開され、情報が誤って暴露される場合があることに注意してください。  
  
## 参照  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [\/errorreport \(Set Error Reporting Behavior\)](../../../csharp/language-reference/compiler-options/errorreport-compiler-option.md)   
 [方法 : プロジェクト プロパティおよび構成設定を変更する](http://msdn.microsoft.com/ja-jp/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)