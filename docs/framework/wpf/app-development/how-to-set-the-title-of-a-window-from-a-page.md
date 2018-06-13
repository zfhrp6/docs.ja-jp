---
title: '方法: ページから、ウィンドウのタイトルを設定'
ms.date: 03/30/2017
helpviewer_keywords:
- windows [WPF], setting title from a page
- title of window [WPF], setting from a page
- pages [WPF], setting window title from
ms.assetid: fecf0d19-3eb6-4f8c-a44f-ff1b6f2b34b3
ms.openlocfilehash: e69812b59783717b7b9c832d4e8ab01ab42827c8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33546186"
---
# <a name="how-to-set-the-title-of-a-window-from-a-page"></a>方法: ページから、ウィンドウのタイトルを設定
この例は、ウィンドウのタイトルを設定する方法を示しています、<xref:System.Windows.Controls.Page>がホストされています。  
  
## <a name="example"></a>例  
 ページを設定してそれをホストしているウィンドウのタイトルを変更することができます、<xref:System.Windows.Controls.Page.WindowTitle%2A>プロパティ、次のようにします。  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowTitleXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowTitlePage.xaml#setpagewindowtitlexaml)]  
  
> [!NOTE]
>  設定、<xref:System.Windows.Controls.Page.Title%2A>ページのプロパティは、ウィンドウのタイトルの値を変更できません。 代わりに、<xref:System.Windows.Controls.Page.Title%2A>ナビゲーション履歴にページのエントリの名前を指定します。
