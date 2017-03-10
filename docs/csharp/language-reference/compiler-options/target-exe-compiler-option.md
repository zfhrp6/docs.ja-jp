---
title: "/target:exe (C# Compiler Options) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "/exe"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "target compiler options [C#], /target:exe"
  - "/target compiler options [C#], /target:exe"
  - "-target compiler options [C#], /target:exe"
ms.assetid: bda5717d-1b91-4848-956b-fcf85c30e432
caps.latest.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 12
---
# /target:exe (C# Compiler Options)
**\/target:exe** オプションは、実行可能な \(EXE\) コンソール アプリケーションを作成するようにコンパイラに指示します。  
  
## 構文  
  
```  
/target:exe  
```  
  
## 解説  
 既定では、**\/target:exe** オプションが有効になっています。  実行可能ファイルは、.exe という拡張子で作成されます。  
  
 Windows プログラムの実行形式を作成するには、[\/target:winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md) を使用します。  
  
 [\/out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) オプションで特に指定しない限り、出力ファイル名は [Main](../../../csharp/programming-guide/main-and-command-args/main-and-command-line-arguments.md) メソッドを含む入力ファイルと同じになります。  
  
 コマンド ラインで指定すると、次の **\/out** または **\/target:module** のオプションまでに指定したすべてのファイルが .exe ファイルを作成するために使用されます。  
  
 **Main** メソッドは、.exe ファイルにコンパイルされるソース コード ファイル内で 1 つだけ必要になります。  [\/main](../../../csharp/language-reference/compiler-options/main-compiler-option.md) コンパイラ オプションを使用すると、コードの複数のクラスに **Main** メソッドが含まれている場合に、どのクラスの **Main** メソッドを使用するのかを指定できます。  
  
### Visual Studio 開発環境でこのコンパイラ オプションを設定するには  
  
1.  プロジェクトの **\[プロパティ\]** ページを開きます。  
  
2.  **\[アプリケーション\]** プロパティ ページをクリックします。  
  
3.  **\[出力の種類\]** プロパティを変更します。  
  
 このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.ProjectProperties3.OutputType%2A>」を参照してください。  
  
## 使用例  
 `in.cs` をコンパイルし、`in.exe` を作成するには、次のいずれかのコマンド ラインを使用します。  
  
```  
csc /target:exe in.cs  
csc in.cs  
```  
  
## 参照  
 [\/target \(Specify Output File Format\)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)   
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)