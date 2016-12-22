---
title: "/optimize (C# Compiler Options) | Microsoft Docs"
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
  - "/optimize"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/optimize compiler option [C#]"
  - "-o compiler option [C#]"
  - "optimize compiler option [C#]"
  - "/o compiler option [C#]"
  - "-optimize compiler option [C#]"
  - "compiler optimization [C#]"
  - "o compiler option [C#]"
ms.assetid: 6dd5b6f2-cd1d-4593-a9f4-1c2ed9404ca0
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /optimize (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

**\/optimize** オプションは、コンパイラで行われる最適化の有効と無効を切り替えて、出力ファイルのサイズを小さくし、速度と効率を高めます。  
  
## 構文  
  
```  
/optimize[+ | -]  
```  
  
## 解説  
 また、**\/optimize** は、実行時にコードを最適化するように共通言語ランタイムに指示します。  
  
 既定では、最適化は無効です。  最適化を有効にするには、**\/optimize\+** を指定します。  
  
 アセンブリで使用するモジュールをビルドする場合は、アセンブリと同じ **\/optimize** の設定を使用してください。  
  
 **\/o** は **\/optimize** の省略形です。  
  
 **\/optimize** オプションと [\/debug](../../../csharp/language-reference/compiler-options/debug-compiler-option.md) オプションを組み合わせることができます。  
  
### Visual Studio 開発環境でこのコンパイラ オプションを設定するには  
  
1.  プロジェクトの **\[プロパティ\]** ページを開きます。  
  
2.  **\[ビルド\]** プロパティ ページをクリックします。  
  
3.  **\[コードの最適化\]** プロパティを変更します。  
  
 このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.CSharpProjectConfigurationProperties3.Optimize%2A>」を参照してください。  
  
## 使用例  
 `t2.cs` をコンパイルし、コンパイラの最適化を有効にするには、次のコードを使用します。  
  
```  
csc t2.cs /optimize  
```  
  
## 参照  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [方法 : プロジェクト プロパティおよび構成設定を変更する](http://msdn.microsoft.com/ja-jp/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)