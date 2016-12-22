---
title: "@ (Specify Response File) (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "@ (Specify Response File) compiler option [Visual Basic]"
ms.assetid: a6847eaa-e5f9-4303-9421-45b55484b9ca
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# @ (Specify Response File) (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

コンパイラ オプションと、コンパイルするソース コード ファイルを含むファイルを指定します。  
  
## 構文  
  
```  
@response_file  
```  
  
## 引数  
 `response_file`  
 必ず指定します。  コンパイラ オプションやコンパイルするソース コード ファイルの一覧を含むファイル。  ファイル名に空白が含まれている場合は、二重引用符 \(" "\) で囲みます。  
  
## 解説  
 コンパイラでは、応答ファイルで指定したコンパイラ オプションとソース コード ファイルをコマンド ラインに指定した場合と同様に処理します。  
  
 コンパイル時に複数の応答ファイルを指定するには、次のように、複数の応答ファイル オプションを指定します。  
  
```  
@file1.rsp @file2.rsp  
```  
  
 応答ファイルでは、複数のコンパイラ オプションとソース コード ファイルを 1 行に記述できます。  1 つのコンパイラ オプションは 1 行に指定する必要があり、複数行にわたって指定できません。  応答ファイルには、シャープ記号 \(`#`\) で始まるコメントを記述できます。  
  
 コマンド ラインに指定したオプションと、1 つ以上の応答ファイルで指定したオプションを組み合わせることができます。  コンパイラでは、検出順にコマンド オプションを処理します。  このため、コマンド ライン引数が、応答ファイルで先に指定したオプションをオーバーライドすることがあります。  逆に、応答ファイルのオプションが、コマンド ラインや他の応答ファイルで先に指定したオプションをオーバーライドすることもあります。  
  
 Visual Basic では、Vbc.exe ファイルと同じディレクトリに Vbc.rsp ファイルがあります。  `/noconfig` オプションが使用されている場合を除き、Vbc.rsp ファイルは既定で含まれています。  詳細については、「[\/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)」を参照してください。  
  
> [!NOTE]
>  `@` オプションは Visual Studio の開発環境内からは利用できません。このオプションを利用できるのは、コマンド ラインからコンパイルするときだけです。  
  
## 使用例  
 サンプルの応答ファイルの一部を次に示します。  
  
```  
# build the first output file  
/target:exe   
/out:MyExe.exe  
source1.vb   
source2.vb  
```  
  
## 使用例  
 次の例では、`@` オプションを `File1.rsp` という応答ファイルで使用する方法を示します。  
  
```  
vbc @file1.rsp  
```  
  
## 参照  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)   
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)