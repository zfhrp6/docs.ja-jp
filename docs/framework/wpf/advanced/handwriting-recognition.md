---
title: "手書き認識 | Microsoft Docs"
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
  - "手書き認識"
  - "認識 (手書きの)"
ms.assetid: f4e8576d-e731-4bac-9818-22e2ae636636
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 手書き認識
ここでは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] プラットフォームでのデジタル インクに関連した認識の基礎について説明します。  
  
## 認識ソリューション  
 <xref:System.Windows.Ink.InkAnalyzer> を使用してインクを認識する方法を次の例に示します。  
  
> [!NOTE]
>  このサンプルでは、手書き認識エンジンをシステムにインストールする必要があります。  
  
 Visual Studio 2005 で、InkRecognition という新しい [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーション プロジェクトを作成します。  Window1.xaml ファイルの内容を次の XAML コードに置き換えます。  このコードは、アプリケーションのユーザー インターフェイスを表示します。  
  
 [!code-xml[InkRecognition#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml#1)]  
  
 WPF インク分析アセンブリ \(IAWinFX.dll、IACore.dll、および IALoader.dll\) への参照を追加します。これらのファイルは、\\Program Files\\Reference Assemblies\\Microsoft\\Tablet PC\\v1.7 にあります。  この分離コード ファイルの内容を次のコードに置き換えます。  
  
 [!code-csharp[InkRecognition#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml.cs#2)]
 [!code-vb[InkRecognition#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InkRecognition/VisualBasic/Window1.xaml.vb#2)]  
  
## 参照  
 <xref:System.Windows.Ink.InkAnalyzer>   
 <xref:System.Windows.Ink.AnalysisStatus>   
 <xref:System.Windows.Controls.InkCanvas>