---
title: "/target:winexe (C# Compiler Options) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "/target:winexe"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/target compiler options [C#], /target:winexe"
  - "-target compiler options [C#], /target:winexe"
  - "target compiler options [C#], /target:winexe"
ms.assetid: b5a0619c-8caa-46a5-a743-1cf68408ad7a
caps.latest.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 11
---
# /target:winexe (C# Compiler Options)
**\/target:winexe** オプションは、実行可能な \(EXE\) Windows プログラムを作成するようにコンパイラに指示します。  
  
## 構文  
  
```  
/target:winexe  
```  
  
## 解説  
 実行可能ファイルは、.exe という拡張子で作成されます。  Windows プログラムは、.NET Framework クラス ライブラリまたは Win32 API のユーザー インターフェイスを提供するプログラムです。  
  
 コンソール アプリケーションを作成するには、[\/target:exe](../../../csharp/language-reference/compiler-options/target-exe-compiler-option.md) を使用します。  
  
 [\/out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) オプションで特に指定しない限り、出力ファイル名は [Main](../../../csharp/programming-guide/main-and-command-args/main-and-command-line-arguments.md) メソッドを含む入力ファイルと同じになります。  
  
 コマンド ラインで指定すると、次の **\/out** オプションまたは [\/target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) オプションまでに指定したすべてのファイルが Windows プログラムの作成に使用されます。  
  
 **Main** メソッドは、.exe ファイルにコンパイルされるソース コード ファイル内で 1 つだけ必要になります。  [\/main](../../../csharp/language-reference/compiler-options/main-compiler-option.md) オプションを使用すると、コードの複数のクラスに **Main** メソッドが含まれている場合に、どのクラスの **Main** メソッドを使用するのかを指定できます。  
  
### Visual Studio 開発環境でこのコンパイラ オプションを設定するには  
  
1.  プロジェクトの **\[プロパティ\]** ページを開きます。  
  
2.  **\[アプリケーション\]** プロパティ ページをクリックします。  
  
3.  **\[出力の種類\]** プロパティを変更します。  
  
 このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.ProjectProperties3.OutputType%2A>」を参照してください。  
  
## 使用例  
 `in.cs` をコンパイルし、Windows プログラムを生成する例を次に示します。  
  
```  
csc /target:winexe in.cs  
```  
  
## 参照  
 [\/target \(Specify Output File Format\)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)   
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)