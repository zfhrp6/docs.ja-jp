---
title: "Windows ランタイムへの URI の引き渡し | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Windows ランタイム、.NET Framework のサポート"
  - "Windows ランタイム, URL を渡す"
ms.assetid: 3eb5ce6f-f304-4f87-8e81-0f25092f5ad4
caps.latest.revision: 10
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 10
---
# Windows ランタイムへの URI の引き渡し
Windows ランタイムのメソッドは絶対 URI だけを受け取ります。[!INCLUDE[wrt](../../../includes/wrt-md.md)] メソッドに相対 URI を渡すと、<xref:System.ArgumentException> 例外がスローされます。 これは、.NET Framework コードで [!INCLUDE[wrt](../../../includes/wrt-md.md)] を使用する場合、[Windows.Foundation.Uri](http://go.microsoft.com/fwlink/p/?LinkId=238376) クラスは Intellisense では <xref:System.Uri?displayProperty=fullName> として示されるためです。<xref:System.Uri?displayProperty=fullName> クラスでは相対 URI を使用できますが、[Windows.Foundation.Uri](http://go.microsoft.com/fwlink/p/?LinkId=238376) クラスでは相対 URI は使用できません。[!INCLUDE[wrt](../../../includes/wrt-md.md)] コンポーネントで公開するメソッドでも同様です。 URI を受け取るメソッドをコンポーネントで公開する場合、コードのシグネチャには <xref:System.Uri?displayProperty=fullName> が含まれます。 ただし、コンポーネントのユーザーに対しては、シグネチャに [Windows.Foundation.Uri](http://go.microsoft.com/fwlink/p/?LinkId=238376) が含まれます。 コンポーネントに渡す URI は、絶対 URI でなければなりません。  
  
 このトピックでは、絶対 URI を検出する方法と、アプリ パッケージ内のリソースを参照するときに絶対 URI を作成する方法を説明します。  
  
## 絶対 URI の検出と使用  
 URI を <xref:System.Uri.IsAbsoluteUri%2A?displayProperty=fullName>に渡す前にそれが絶対 URI であることを確認するには、[!INCLUDE[wrt](../../../includes/wrt-md.md)] プロパティを使用します。 このプロパティを使用する方が、<xref:System.ArgumentException> 例外をキャッチして処理するより効率的です。  
  
## アプリ パッケージのリソースに対する絶対 URI の使用  
 アプリのパッケージに含まれるリソースに対して URI を指定するには、`ms-appx` スキームまたは `ms-appx-web` スキームを使用して絶対 URI を作成します。  
  
 次の例に、XAML とコードの両方を使用して、Pages という名前のフォルダーに含まれるリソースに、[WebView](http://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.webview.aspx) コントロールの [Source](http://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.webview.source.aspx) プロパティと [Image](http://msdn.microsoft.com/library/windows/apps/br242752.aspx) コントロールの [Source](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.image.source.aspx) プロパティを設定する方法を示します。  
  
 [!code-xml[System.URIToWindowsURI#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml#1)]  
[!code-csharp[System.URIToWindowsURI#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml.cs#2)]
[!code-vb[System.URIToWindowsURI#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.uritowindowsuri/vb/mainpage.xaml.vb#2)]  
  
 これらのスキームの詳細については、Windows デベロッパー センターの「[URI スキーム](http://msdn.microsoft.com/library/windows/apps/jj655406.aspx)」を参照してください。  
  
## 参照  
 [Windows ストア アプリおよび Windows ランタイムのための .NET Framework サポート](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)