---
title: "/target:library (C# Compiler Options) | Microsoft Docs"
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
  - "/dll"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "-target compiler options [C#], /target:library"
  - "target compiler options [C#], /target:library"
  - "/target compiler options [C#], /target:library"
ms.assetid: c5670e88-2126-47c1-8d1c-217923837d17
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /target:library (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

**\/target:library** オプションは、実行可能ファイル \(EXE\) ではなくダイナミック リンク ライブラリ \(DLL: Dynamic\-Link Library\) を作成するようにコンパイラに指示します。  
  
## 構文  
  
```  
/target:library  
```  
  
## 解説  
 作成される DLL の拡張子は .dll です。  
  
 [\/out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) オプションで指定しない限り、出力ファイル名は最初の入力ファイルと同じになります。  
  
 コマンド ラインで指定すると、次の **\/out** または **\/target:module** のオプションまでに指定したすべてのファイルが .dll ファイルを作成するために使用されます。  
  
 .dll ファイルのビルドには、[Main](../../../csharp/programming-guide/main-and-command-args/main-and-command-line-arguments.md) メソッドは不要です。  
  
### Visual Studio 開発環境でこのコンパイラ オプションを設定するには  
  
1.  プロジェクトの **\[プロパティ\]** ページを開きます。  
  
2.  **\[アプリケーション\]** プロパティ ページをクリックします。  
  
3.  **\[出力の種類\]** プロパティを変更します。  
  
 このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.ProjectProperties3.OutputType%2A>」を参照してください。  
  
## 使用例  
 `in.cs` をコンパイルし、`in.dll` を作成するには、次のコードを使用します。  
  
```  
csc /target:library in.cs  
```  
  
## 参照  
 [\/target \(Specify Output File Format\)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)   
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)