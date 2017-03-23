---
title: "@ (C# Compiler Options) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "@"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "response files, specifying for compilation [C#]"
  - "@ compiler option"
ms.assetid: dda4fa9f-a02c-400f-8b6a-d58834e13d7f
caps.latest.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 9
---
# @ (C# Compiler Options)
@ オプションを使用すると、コンパイラ オプションおよびコンパイルするソース コード ファイルを含むファイルを指定できます。  
  
## 構文  
  
```  
@response_file  
```  
  
## Arguments  
 `response_file`  
 コンパイラ オプションやコンパイルするソース コード ファイルの一覧を含むファイル。  
  
## 解説  
 コンパイラ オプションとソース コード ファイルは、コマンド ラインで指定した場合と同じように、コンパイラによって処理されます。  
  
 コンパイル時に複数の応答ファイルを指定するには、複数の応答ファイル オプションを指定します。  たとえば、次のようになります。  
  
```  
@file1.rsp @file2.rsp  
```  
  
 応答ファイルでは、複数のコンパイラ オプションとソース コード ファイルを 1 行に記述できます。  1 つのコンパイラ オプションは 1 行に指定する必要があり、複数行にわたって指定できません。  応答ファイルには、シャープ記号 \(\#\) で始まるコメントを記述できます。  
  
 応答ファイルでのコンパイラ オプションの指定方法は、コマンド ラインでのコンパイラ オプションの指定方法と同じです。  詳細については、「[コマンド ラインからのビルド](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)」を参照してください。  
  
 コンパイラでは、検出順にコマンド オプションを処理します。  このため、コマンド ライン引数によって、応答ファイルで先に指定したオプションをオーバーライドできます。  逆に、応答ファイルのオプションが、コマンド ラインや他の応答ファイルで先に指定したオプションをオーバーライドすることもあります。  
  
 C\# では、csc.exe ファイルと同じディレクトリに csc.rsp ファイルがあります。  csc.rsp の詳細については、「[\/noconfig \(csc.rsp の無視\)](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md)」を参照してください。  
  
 このコンパイラ オプションは、Visual Studio 開発環境で設定することも、プログラムから変更することもできません。  
  
## 使用例  
 サンプルの応答ファイルの一部を次に示します。  
  
```  
# build the first output file  
/target:exe /out:MyExe.exe source1.cs source2.cs  
```  
  
## 参照  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)