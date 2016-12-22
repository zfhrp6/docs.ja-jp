---
title: "A reference was created to embedded interop assembly &#39;&lt;assembly1&gt;&#39; because of an indirect reference to that assembly from assembly &#39;&lt;assembly2&gt;&#39; | Microsoft Docs"
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
  - "vbc40059"
  - "bc40059"
helpviewer_keywords: 
  - "VBC40059"
  - "BC40059"
ms.assetid: 520e39cb-8ab6-46f5-aa00-08afd51b4b7c
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# A reference was created to embedded interop assembly &#39;&lt;assembly1&gt;&#39; because of an indirect reference to that assembly from assembly &#39;&lt;assembly2&gt;&#39;
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

埋め込まれた相互運用機能アセンブリ '\<assembly1\>' への参照が作成されました。これは、そのアセンブリへの間接参照がアセンブリ '\<assembly2\>' によって作成されたためです。どちらかのアセンブリで '相互運用機能型の埋め込み' プロパティを変更することを検討してください。  
  
 `Embed Interop Types` プロパティが `True` に設定されたアセンブリ \(assembly1\) に参照を追加しました。  これにより、コンパイラは、このアセンブリから相互運用機能の型情報を埋め込むよう指示されます。  ただし、参照していた別のアセンブリ \(assembly2\) もこのアセンブリ \(assembly1\) を参照しており、また `Embed Interop Types` プロパティが `False` に設定されているため、コンパイラはこのアセンブリから相互運用機能の型情報を埋め込むことができません。  
  
> [!NOTE]
>  アセンブリ参照の `Embed Interop Types` プロパティを `True` に設定することは、コマンド ライン コンパイラの `/link` オプションを使用してアセンブリを参照することと同じです。  
  
 **エラー ID:** BC40059  
  
### この警告に対処するには  
  
-   両方のアセンブリに相互運用の型情報を埋め込むには、assembly1 へのすべての参照の `Embed Interop Types` プロパティを `True` に設定します。  
  
-   assembly1 の `Embed Interop Types` プロパティを `False` に設定すると警告を回避できます。  この場合、相互運用の型情報はプライマリ相互機能アセンブリ \(PIA\) により提供されます。  
  
## 参照  
 [\/link](../../../visual-basic/reference/command-line-compiler/link.md)   
 [Programming with Primary Interop Assemblies](http://msdn.microsoft.com/ja-jp/306fa1d6-0703-4004-9e93-d0a57f1be81e)