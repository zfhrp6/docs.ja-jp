---
title: "/target:appcontainerexe (C# コンパイラ オプション) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
ms.assetid: e7e62229-23ea-4e53-bef5-380d951bf95f
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /target:appcontainerexe (C# コンパイラ オプション)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

**\/target:appcontainerexe** コンパイラ オプションを使用すると、コンパイラはアプリケーション コンテナーで実行する必要のある Windows 実行可能ファイル \(.exe\) を作成します。  このオプションは [\/target:winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md) に相当しますが、[!INCLUDE[win8_appname_long](../../../csharp/includes/win8_appname_long_md.md)] のアプリケーション用に設計されています。  
  
## 構文  
  
```  
/target:appcontainerexe  
```  
  
## 解説  
 アプリケーション コンテナーでのアプリケーションの実行を要求するために、このオプションは、[Portable Executable](http://go.microsoft.com/fwlink/p/?LinkId=236960) \(PE\) ファイルでビットを設定します。  このビットが設定されている場合、CreateProcess メソッドがアプリケーション コンテナー外の実行可能ファイルを起動しようとすると、エラーが発生します。  
  
 [\/out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) オプションを使用しない限り、出力ファイル名は [Main](../../../csharp/programming-guide/main-and-command-args/main-and-command-line-arguments.md) メソッドを含む入力ファイルと同じになります。  
  
 コマンド プロンプトでこのオプションを指定すると、次の **\/out** または **\/target** オプションまでのすべてのファイルが、実行可能ファイルを作成するために使用されます。  
  
### IDE でこのコンパイラ オプションを設定するには  
  
1.  **ソリューション エクスプローラー**で、プロジェクトのショートカット メニューを開き、**\[プロパティ\]** をクリックします。  
  
2.  **\[アプリケーション\]** タブの **\[出力の種類\]** ボックスの一覧で、**\[Windows ストア アプリ\]** をクリックします。  
  
     このオプションは [!INCLUDE[win8_appname_long](../../../csharp/includes/win8_appname_long_md.md)] アプリケーション テンプレートでのみ使用できます。  
  
 このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.ProjectProperties3.OutputType%2A>」を参照してください。  
  
## 使用例  
 次のコマンドは、アプリケーション コンテナーでのみ実行できる Windows 実行可能ファイルに `filename.cs` をコンパイルします。  
  
```  
csc /target:appcontainerexe filename.cs  
```  
  
## 参照  
 [\/target \(Specify Output File Format\)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)   
 [\/target:winexe \(Create a Windows Program\)](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md)   
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)