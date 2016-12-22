---
title: "方法 : レガシ エンコーディングと Unicode の間で変換を行う (C# プログラミング ガイド) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "変換 [C#], レガシ エンコーディングから Unicode エンコーディングへ"
  - "文字列 [C#], 変換 (エンコーディング間の)"
ms.assetid: 4eed7d8e-47ab-4a7c-8b95-9645a0ef000b
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 方法 : レガシ エンコーディングと Unicode の間で変換を行う (C# プログラミング ガイド)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

C\# では、メモリ内の文字列はすべて Unicode \(UTF\-16\) としてエンコードされます。  データをストレージから `string` オブジェクトに取り込むと、データは UTF\-16 に自動的に変換されます。  データに 0 ～ 127 の ASCII 値のみが含まれる場合、変換の際にユーザー側が特別な処理を行う必要はありません。  ただし、ソース テキストに拡張 ASCII バイト値 \(128 ～ 255\) が含まれる場合、拡張文字は既定で現在のコード ページに従って解釈されます。  ソース テキストが別のコード ページに従って解釈されるように指定するには、次の例に示すように、<xref:System.Text.Encoding?displayProperty=fullName> クラスを使用します。  
  
## 使用例  
 8 ビット ASCII でエンコードされているテキスト ファイルを変換し、Windows コード ページ 737 に従ってソース テキストを解釈する方法を次の例に示します。  
  
 [!code-cs[csProgGuideStrings#34](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-convert-between-legacy-encodings-and-unicode_1.cs)]  
  
## 参照  
 [文字列](../../../csharp/programming-guide/strings/index.md)