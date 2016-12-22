---
title: "Friend assembly reference &lt;reference&gt; is invalid | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31535"
  - "bc31535"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC31535"
ms.assetid: 6540c1d0-bb19-4051-a579-2e4f9094585e
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Friend assembly reference &lt;reference&gt; is invalid
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

フレンド アセンブリ参照 \<reference\> は無効です。厳密な名前の署名つきアセンブリはその InternalsVisibleTo 宣言内で公開キーを指定しなければなりません。  
  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 属性コンストラクターに渡すアセンブリ名では、厳密な名前のアセンブリが指定されていますが、`PublicKey` 属性が含まれていません。  
  
 **エラー ID:** BC31535  
  
### このエラーを解決するには  
  
1.  厳密な名前のフレンド アセンブリの公開キーを確認します。  `PublicKey` 属性を使用して、<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 属性コンストラクターに渡すアセンブリ名にその公開キーを組み込みます。  
  
## 参照  
 <xref:System.Reflection.AssemblyName>   
 [フレンド アセンブリ](../Topic/Friend%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md)   
 [方法: 署名されたフレンド アセンブリを作成する](../Topic/How%20to:%20Create%20Signed%20Friend%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md)