---
title: "方法 : インク データにカスタム データを追加する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "インク データ, 追加 (カスタム データを)"
  - "InkCanvas, 表示"
ms.assetid: f02aac6f-3436-4f7c-b6ea-0452cba5332c
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# 方法 : インク データにカスタム データを追加する
インクが Ink Serialized Format \(ISF\) として保存されるときに保存されるインクにカスタム データを追加できます。  カスタム データは、<xref:System.Windows.Ink.DrawingAttributes>、<xref:System.Windows.Ink.StrokeCollection>、または <xref:System.Windows.Ink.Stroke> に保存できます。  3 つのオブジェクトにカスタム データを保存できるため、データを保存する最善の場所を選択することが可能になります。  カスタム データの格納とアクセスに使用するメソッドは、3 つのいずれのクラスでもほぼ同じです。  
  
 カスタム データとして保存できるのは、次の型だけです。  
  
-   <xref:System.Boolean>  
  
-   <xref:System.Boolean>\[\]  
  
-   <xref:System.Byte>  
  
-   <xref:System.Byte>\[\]  
  
-   <xref:System.Char>  
  
-   <xref:System.Char>\[\]  
  
-   <xref:System.DateTime>  
  
-   <xref:System.DateTime>\[\]  
  
-   <xref:System.Decimal>  
  
-   <xref:System.Decimal>\[\]  
  
-   <xref:System.Double>  
  
-   <xref:System.Double>\[\]  
  
-   <xref:System.Int16>  
  
-   <xref:System.Int16>\[\]  
  
-   <xref:System.Int32>  
  
-   <xref:System.Int32>\[\]  
  
-   <xref:System.Int64>  
  
-   <xref:System.Int64>\[\]  
  
-   <xref:System.Single>  
  
-   <xref:System.Single>\[\]  
  
-   <xref:System.String>  
  
-   <xref:System.UInt16>  
  
-   <xref:System.UInt16>\[\]  
  
-   <xref:System.UInt32>  
  
-   <xref:System.UInt32>\[\]  
  
-   <xref:System.UInt64>  
  
-   <xref:System.UInt64>\[\]  
  
## 使用例  
 <xref:System.Windows.Ink.StrokeCollection> にカスタム データを追加したり、そこからカスタム データを取得したりする方法を次の例に示します。  
  
 [!code-csharp[HowToAddCustomDataToInk#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml.cs#1)]  
  
 次の例では、<xref:System.Windows.Controls.InkCanvas> と 2 つのボタンを表示するアプリケーションを作成します。  `switchAuthor` ボタンを使用すると、2 人の作成者がそれぞれ異なるペンを使用できます。  `changePenColors` ボタンは、作成者に応じて <xref:System.Windows.Controls.InkCanvas> 上の各ストロークの色を変更します。  このアプリケーションでは、2 つの <xref:System.Windows.Ink.DrawingAttributes> オブジェクトを定義し、<xref:System.Windows.Ink.Stroke> を描画した作成者を示すカスタム プロパティをそれぞれに追加します。  ユーザーが `changePenColors` をクリックすると、アプリケーションは、カスタム プロパティの値に従ってストロークの外観を変更します。  
  
 [!code-xml[HowToAddCustomDataToInk#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml#2)]  
  
 [!code-csharp[HowToAddCustomDataToInk#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml.cs#3)]