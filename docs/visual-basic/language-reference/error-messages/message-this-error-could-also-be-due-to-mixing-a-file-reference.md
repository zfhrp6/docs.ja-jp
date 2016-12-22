---
title: "&lt;message&gt; このエラーは、ファイル参照とアセンブリ &#39;&lt;assemblyname&gt;&#39; へのプロジェクト参照との混合によって生じた可能性があります | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30971"
  - "vbc30971"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30971"
ms.assetid: 75d2e8b5-2fdc-4623-8b32-cba805dab7db
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;message&gt; このエラーは、ファイル参照とアセンブリ &#39;&lt;assemblyname&gt;&#39; へのプロジェクト参照との混合によって生じた可能性があります
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

\<message\> このエラーは、ファイル参照とアセンブリ '\<assemblyname\>' へのプロジェクト参照との混合によって生じた可能性があります。 この場合、プロジェクト '\<projectname1\>' の '\<assemblyfilename\>' へのファイル参照を '\<projectname2\>' へのプロジェクト参照で置き換えてください。  
  
 プロジェクト内のコードが別のプロジェクトのメンバーにアクセスしていますが、このプロジェクトのソリューションは [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] コンパイラに参照の解決を許可するよう構成されていません。  
  
 別のアセンブリで定義されている型にアクセスするには、そのアセンブリへの参照を [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] コンパイラが保持する必要があります。 これは、プロジェクト間の循環参照にならない、単一であいまいさのない参照である必要があります。  
  
 **エラー ID:** BC30971  
  
### このエラーを解決するには  
  
1.  どのプロジェクトが、プロジェクトからの参照に最適なアセンブリを作成しているか特定します。 この判断には、ファイル アクセスの容易さや更新の頻度などの基準を使用できます。  
  
2.  プロジェクトのプロパティに、使用する型が定義されているアセンブリを含むプロジェクトへの参照を追加します。  
  
## 参照  
 [プロジェクト内の参照の管理](/visual-studio/ide/managing-references-in-a-project)   
 [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [NIB 方法: &#91;参照の追加&#93; ダイアログ ボックスを使用して参照を追加または削除する](http://msdn.microsoft.com/ja-jp/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [NIB 方法: プロジェクト プロパティおよび構成設定を変更する](http://msdn.microsoft.com/ja-jp/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [壊れた参照のトラブルシューティング](/visual-studio/ide/troubleshooting-broken-references)