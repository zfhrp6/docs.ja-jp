---
title: "/langversion (Visual Basic) | Microsoft Docs"
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
  - "/langversion compiler option [Visual Basic]"
  - "langversion compiler option [Visual Basic]"
  - "-langversion compiler option [Visual Basic]"
ms.assetid: 59b7b0c8-2dde-4e9b-94e7-0237f7e0bafb
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 8
---
# /langversion (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

コンパイラが、指定された言語バージョンの Visual Basic に含まれる構文のみを受け入れるようにします。  
  
## 構文  
  
```  
/langversion:version  
```  
  
## 引数  
 `version`  
 必ず指定します。  コンパイル中に使用する言語バージョンを示します。  指定できる値は `9`、`9.0`、`10`、および `10.0` です。  
  
## 解説  
 `/langversion` オプションは、コンパイラが受け入れる構文を指定します。  たとえば、言語バージョンが 9.0 であることを指定すると、バージョン 10.0 以降でのみ有効な構文に対し、コンパイラでエラーが生成されます。  
  
 このオプションは、異なるバージョンの .NET Framework を対象とするアプリケーションを開発する場合に使用できます。  たとえば、.NET Framework 3.5 を対象とする場合、このオプションを使用することで、言語バージョン 10.0 からの構文を使用しないことを保証できます。  
  
 `/langversion` は、コマンド ラインからのみ直接設定できます。  詳細については、「[対象となる特定の .NET Framework バージョンの指定](/visual-studio/ide/targeting-a-specific-dotnet-framework-version)」を参照してください。  
  
## 使用例  
 次のコードでは、Visual Basic 9.0 の `sample.vb` をコンパイルします。  
  
```  
vbc /langversion:9.0 sample.vb  
```  
  
## 参照  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [対象となる特定の .NET Framework バージョンの指定](/visual-studio/ide/targeting-a-specific-dotnet-framework-version)