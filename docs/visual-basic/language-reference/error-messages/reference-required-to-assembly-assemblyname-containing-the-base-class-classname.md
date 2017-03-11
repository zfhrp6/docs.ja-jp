---
title: "基底クラス &#39;&lt;classname&gt;&#39; を含むアセンブリ &#39;&lt;assemblyname&gt;&#39; への参照が必要です。 | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc30007"
  - "vbc30007"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30007"
ms.assetid: 5f34cf47-6c6e-4954-bd8e-d6b020b75fb7
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# 基底クラス &#39;&lt;classname&gt;&#39; を含むアセンブリ &#39;&lt;assemblyname&gt;&#39; への参照が必要です。
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

基底クラス '\<classname\>' を含むアセンブリ '\<assemblyname\>' への参照が必要です。 プロジェクトに参照を追加してください。  
  
 プロジェクト内で直接参照されないダイナミック リンク ライブラリ \(DLL\) またはアセンブリでクラスが定義されています。[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] コンパイラでは、クラスが複数の DLL またはアセンブリで定義されている場合に備えて、あいまいさを避けるための参照が必要になります。  
  
 **エラー ID:** BC30007  
  
### このエラーを解決するには  
  
-   参照されない DLL またはアセンブリの名前をプロジェクト参照に含めます。  
  
## 参照  
 [NIB 方法: &#91;参照の追加&#93; ダイアログ ボックスを使用して参照を追加または削除する](http://msdn.microsoft.com/ja-jp/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [プロジェクト内の参照の管理](/visual-studio/ide/managing-references-in-a-project)   
 [壊れた参照のトラブルシューティング](/visual-studio/ide/troubleshooting-broken-references)