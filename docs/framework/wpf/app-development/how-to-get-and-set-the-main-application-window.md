---
title: "方法: を取得し、アプリケーションのメイン ウィンドウの設定"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- windows objects [WPF], setting
- setting windows objects [WPF]
- windows objects [WPF], getting
- getting windows objects [WPF]
ms.assetid: ec902bc4-4a59-46f5-8ec1-963b46789356
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0d6bca158172fd3fc31526287c6d4a9928a8ea0c
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-get-and-set-the-main-application-window"></a>方法: を取得し、アプリケーションのメイン ウィンドウの設定
この例では、取得し、アプリケーションのメイン ウィンドウを設定する方法を示します。  
  
## <a name="example"></a>例  
 最初の<xref:System.Windows.Window>内でインスタンス化されている、[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)]によってアプリケーションが自動的に設定<xref:System.Windows.Application>アプリケーションのメイン ウィンドウとして。 最初の<xref:System.Windows.Window>スタートアップとして指定されているウィンドウをインスタンス化は、通常にある[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)](を参照してください<xref:System.Windows.Application.StartupUri%2A>)。  
  
 最初の<xref:System.Windows.Window>コードを使用してインスタンス可能性があります。 1 つの例は、ウィンドウを開き、次のように、アプリケーションの起動時に。  
  
 [!code-csharp[HOWTOWindowManagementSnippets#FirstWindowUsingCodeCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/App.xaml.cs#firstwindowusingcodecodebehind)]
 [!code-vb[HOWTOWindowManagementSnippets#FirstWindowUsingCodeCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/application.xaml.vb#firstwindowusingcodecodebehind)]  
  
 場合によっては、最初のインスタンス化される<xref:System.Windows.Window>が実際にアプリケーションのメイン ウィンドウなど、スプラッシュ スクリーン。 この例では、次のようなマークアップを使用してアプリケーションのメイン ウィンドウを指定できます。  
  
 [!code-xaml[ApplicationMainWindowSnippets#SetApplicationMainWindowXAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/ApplicationMainWindowSnippets/XAML/App.xaml#setapplicationmainwindowxaml)]  
  
 メイン ウィンドウを自動または手動で指定するかどうかは、メイン ウィンドウからを取得できます<xref:System.Windows.Application.MainWindow%2A>次のように、次のコードを使用します。  
  
 [!code-csharp[ApplicationMainWindowSnippets#GetApplicationMainWindowCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationMainWindowSnippets/CSharp/App.xaml.cs#getapplicationmainwindowcode)]
 [!code-vb[ApplicationMainWindowSnippets#GetApplicationMainWindowCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationMainWindowSnippets/visualbasic/application.xaml.vb#getapplicationmainwindowcode)]
