---
title: "/codepage (C# Compiler Options) | Microsoft Docs"
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
  - "/codepage"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/codepage compiler option [C#]"
  - "codepage compiler option [C#]"
  - "-codepage compiler option [C#]"
ms.assetid: 75942989-b69a-4308-90a0-840c73d2c478
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /codepage (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

このオプションは、コンパイル時に使用するコード ページを指定します。システムで現在使用されている既定のコードページ以外のコードページを使用する場合に使用します。  
  
## 構文  
  
```  
/codepage:id  
```  
  
## Arguments  
 `id`  
 コンパイル時にすべてのソース コード ファイルで使うコード ページの ID。  
  
## 解説  
 コンピューターの既定のコード ページを使わずに作成されたソース コード ファイルをコンパイルする場合は、**\/codepage** オプションで使用するコード ページを指定できます。  **\/codepage** は、コンパイル時にすべてのソース コード ファイルに適用されます。  
  
 ソース コードの作成時に使用されたコード ページがコンピューターで有効なコード ページと同じ場合、または UNICODE か UTF\-8 の場合は、**\/codepage** を使う必要はありません。  
  
 コード ページが [GetCPInfo](http://go.microsoft.com/fwlink/?LinkId=148371) システムでサポートされるかを見つける方法については、"参照してください。  
  
 このコンパイラ オプションは、Visual Studio で利用できず、プログラムで変更することもできません。  
  
## 参照  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [方法 : プロジェクト プロパティおよび構成設定を変更する](http://msdn.microsoft.com/ja-jp/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)