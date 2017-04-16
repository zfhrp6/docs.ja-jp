---
title: "方法 : アプリケーション ジェスチャを認識する | Microsoft Docs"
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
  - "アプリケーション ジェスチャ, 認識"
  - "ジェスチャ, 認識"
ms.assetid: d58b740f-5192-4a3e-af59-7aa162e6ca15
caps.latest.revision: 4
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 4
---
# 方法 : アプリケーション ジェスチャを認識する
ユーザーが <xref:System.Windows.Controls.InkCanvas> で <xref:System.Windows.Ink.ApplicationGesture> ジェスチャを作成した場合に、インクを消去する方法を次の例に示します。  この例では、`inkCanvas1` という名前の <xref:System.Windows.Controls.InkCanvas> が、XAML ファイル内で宣言されていることを前提としています。  
  
## 使用例  
 [!code-csharp[HowToRecognizeGestures#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToRecognizeGestures/CSharp/Window1.xaml.cs#1)]
 [!code-vb[HowToRecognizeGestures#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToRecognizeGestures/VisualBasic/Window1.xaml.vb#1)]  
  
## 参照  
 <xref:System.Windows.Ink.ApplicationGesture>   
 <xref:System.Windows.Controls.InkCanvas>   
 <xref:System.Windows.Controls.InkCanvas.Gesture>