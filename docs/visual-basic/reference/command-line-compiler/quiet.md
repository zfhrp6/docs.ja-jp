---
title: "/quiet | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "/quiet"
  - "quiet"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "-quiet compiler option [Visual Basic]"
  - "/quiet compiler option [Visual Basic]"
  - "quiet compiler option [Visual Basic]"
ms.assetid: 5d77fa23-4c50-4708-8535-649912b098e8
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# /quiet
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

構文関連のエラーおよび警告に関するコードが表示されないようにします。  
  
## 構文  
  
```  
/quiet  
```  
  
## 解説  
 既定では、`/quiet` は無効です。  コンパイラは、構文関連のエラーまたは警告を報告するときに、ソース コード行も出力します。  コンパイラの出力を解析するアプリケーションの場合、診断テキストだけがコンパイラから出力される方が便利な場合があります。  
  
 次の例の場合、`/quiet` を指定せずにコンパイルを行うと、`Module1` からはソース コードを含むエラーが出力されます。  
  
```  
Module Module1  
    Sub Main()  
        x()  
    End Sub  
End Module  
```  
  
 出力  
  
 `E:\test\t2.vb(3) : error BC30451: Name 'x' is not declared.`  
  
 `x`  
  
 `~`  
  
 `/quiet` を指定してコンパイルを行うと、コンパイラからの出力は次の行だけになります。  
  
 `E:\test\t2.vb(3) : error BC30451: Name 'x' is not declared.`  
  
> [!NOTE]
>  `/quiet` オプションは Visual Studio の開発環境内からは利用できません。このオプションを利用できるのは、コマンド ラインからコンパイルするときだけです。  
  
## 使用例  
 次に示すのは、`T2.vb` をコンパイルし、構文関連のコンパイラ診断に対してコードを表示しない場合のコード例です。  
  
```  
vbc /quiet t2.vb  
```  
  
## 参照  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)