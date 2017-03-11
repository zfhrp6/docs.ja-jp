---
title: "/recurse | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "/recurse compiler option [Visual Basic]"
  - "-recurse compiler option [Visual Basic]"
  - "recurse compiler option [Visual Basic]"
ms.assetid: 84a0b670-33ae-44c4-a46a-b90388809317
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 12
---
# /recurse
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

指定ディレクトリまたはプロジェクト ディレクトリのすべての子ディレクトリ内のソース コード ファイルをコンパイルします。  
  
## 構文  
  
```  
/recurse:[dir\]file  
```  
  
## 引数  
 `dir`  
 省略可能です。  検索を開始するディレクトリ。  ディレクトリを指定しない場合は、プロジェクト ディレクトリから検索されます。  
  
 `file`  
 必ず指定します。  検索するファイル。  ワイルドカード文字を使用できます。  
  
## 解説  
 `/recurse` を使用しなくても、ファイル名にワイルドカードを使用すると、プロジェクト ディレクトリ内で一致するすべてのファイルをコンパイルできます。  出力ファイル名を指定しないと、処理する最初の入力ファイルに基づいて、コンパイラで出力ファイル名が指定されます。  通常は、コンパイル対象のファイルの一覧をアルファベット順に表示したときの最初のファイル名が使用されます。  このため、`/out` オプションを使用して出力ファイルを指定することをお勧めします。  
  
> [!NOTE]
>  `/recurse` オプションは Visual Studio の開発環境内からは利用できません。このオプションを利用できるのは、コマンド ラインからコンパイルするときだけです。  
  
## 使用例  
 現在のディレクトリにあるすべての [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] ファイルをコンパイルする場合のコード例です。  
  
```  
vbc *.vb  
```  
  
 `Test\ABC` ディレクトリおよびその下の全ディレクトリ内の [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] ファイルをすべてコンパイルし、`Test.ABC.dll` を生成する場合のコード例を次に示します。  
  
```  
vbc /target:library /out:Test.ABC.dll /recurse:Test\ABC\*.vb  
```  
  
## 参照  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/out](../../../visual-basic/reference/command-line-compiler/out.md)   
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)