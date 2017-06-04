---
title: "グラフィックス コンテナーの使用 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "例 [Windows フォーム], グラフィックス コンテナー"
  - "グラフィックス コンテナー"
  - "グラフィックス, 使用 (コンテナーを)"
ms.assetid: 74632f91-cefa-4f51-ab7c-f9ac91942caf
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# グラフィックス コンテナーの使用
ベクター イメージ、ラスター イメージ、およびテキストを表示するために、<xref:System.Drawing.Graphics> オブジェクトには <xref:System.Drawing.Graphics.DrawLine%2A>、<xref:System.Drawing.Graphics.DrawImage%2A>、<xref:System.Drawing.Graphics.DrawString%2A> などのメソッドが用意されています。  <xref:System.Drawing.Graphics> オブジェクトは、描画される項目の画質や方向に影響を与える複数のプロパティも保持しています。  たとえば、スムージング モード プロパティは直線や曲線に対してアンチエイリアシングが適用されるかどうかを指定し、ワールド変換プロパティは描画対象項目の位置および回転に影響を与えます。  
  
 <xref:System.Drawing.Graphics> オブジェクトは、特定のディスプレイ デバイスに関連付けられています。  <xref:System.Drawing.Graphics> オブジェクトを使用してウィンドウ内で描画を行うと、その <xref:System.Drawing.Graphics> オブジェクトはそのウィンドウに関連付けられます。  
  
 <xref:System.Drawing.Graphics> オブジェクトは、描画に影響を与える一連のプロパティを保持し、デバイス固有の情報にリンクされるため、コンテナーとして考えることができます。  既存の <xref:System.Drawing.Graphics> オブジェクトの <xref:System.Drawing.Graphics.BeginContainer%2A> メソッドを呼び出すことによって、その <xref:System.Drawing.Graphics> オブジェクト内に第 2 のコンテナーを作成できます。  
  
## このセクションの内容  
 [Graphics オブジェクトの状態の管理](../../../../docs/framework/winforms/advanced/managing-the-state-of-a-graphics-object.md)  
 <xref:System.Drawing.Graphics> オブジェクトの画質設定、クリッピング領域、および変換を管理する方法について説明します。  
  
 [入れ子になっているグラフィックス コンテナーの使用](../../../../docs/framework/winforms/advanced/using-nested-graphics-containers.md)  
 コンテナーを使用して <xref:System.Drawing.Graphics> オブジェクトの状態を制御する方法を示します。