---
title: "方法: 移動履歴を前後へ移動する | Microsoft Docs"
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
  - "履歴, 移動, 移動 (前方へ)"
  - "移動, ナビゲーション履歴 (前方)"
ms.assetid: 5939d574-5f53-469e-85f5-1f2b13607caa
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 方法: 移動履歴を前後へ移動する
この例では" 進む " ナビゲーション履歴のエントリに移動する方法を示します。  
  
## 使用例  
 次のコンテンツをホストから実行がナビゲーション履歴を転送します。またはその逆を移動できること 1 エントリずつコードします。  
  
-   <xref:System.Windows.Navigation.NavigationService> を使用して <xref:System.Windows.Navigation.NavigationWindow>  
  
-   <xref:System.Windows.Navigation.NavigationService> を使用して <xref:System.Windows.Controls.Frame>  
  
-   [!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)]  
  
 1 エントリ前方に移動する前にまず **CanGoForward** のプロパティを調べることによって" 進む " ナビゲーション履歴にエントリ実行することを確認する必要があります。  前方に移動するには**GoForward** 1 エントリのメソッドを呼び出します。  この操作を次の例に示します。  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateForwardCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigateforwardcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateForwardCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigateforwardcode)]  
  
 1 エントリを移動する前に**CanGoBack** のプロパティを調べることによって" 戻る " ナビゲーション履歴にエントリ実行することを確認する必要があります。  1 エントリを移動するには**GoBack** のメソッドを呼び出します。  この操作を次の例に示します。  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateBackCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigatebackcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateBackCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigatebackcode)]  
  
 **CanGoForward** **GoForward** **CanGoBack** と **GoBack** は <xref:System.Windows.Navigation.NavigationWindow><xref:System.Windows.Controls.Frame> と <xref:System.Windows.Navigation.NavigationService> によって実装されます。  
  
> [!NOTE]
>  **GoForward** と " 進む " ナビゲーション履歴にエントリが呼び出すと**GoBack** を呼び出すと戻る " ナビゲーション履歴にエントリがない場合<xref:System.InvalidOperationException> がスローされます。