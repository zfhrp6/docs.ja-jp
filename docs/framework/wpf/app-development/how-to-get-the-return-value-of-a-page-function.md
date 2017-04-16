---
title: "方法 : ページ関数の戻り値を取得する | Microsoft Docs"
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
  - "関数, 取得 (戻り値を)"
  - "取得, ページ関数の戻り値"
  - "ページ関数, 取得 (戻り値を)"
  - "ページ関数の戻り値"
ms.assetid: 75470af6-256c-4c46-87e7-705080723a1c
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# 方法 : ページ関数の戻り値を取得する
この例では、ページ関数から返された結果を取得する方法を示します。  
  
## 使用例  
 ページ関数から返された結果を取得するには、呼び出し先のページ関数の <xref:System.Windows.Navigation.PageFunction%601.Return> を処理する必要があります。  
  
 [!code-xml[HOWTOPageFunctionSnippets#CallAPageFunctionXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/CSharp/CallingPage.xaml#callapagefunctionxaml)]  
  
 [!code-csharp[HOWTOPageFunctionSnippets#GetPageFunctionResultCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/CSharp/CallingPage.xaml.cs#getpagefunctionresultcodebehind)]
 [!code-vb[HOWTOPageFunctionSnippets#GetPageFunctionResultCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOPageFunctionSnippets/VisualBasic/CallingPage.xaml.vb#getpagefunctionresultcodebehind)]  
  
## 参照  
 <xref:System.Windows.Navigation.PageFunction%601>