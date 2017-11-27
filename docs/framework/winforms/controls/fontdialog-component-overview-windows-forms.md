---
title: "FontDialog コンポーネントの概要 (Windows フォーム)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: FontDialog
helpviewer_keywords:
- Font dialog box [Windows Forms], Windows Forms
- Font dialog box
- FontDialog component [Windows Forms], about FontDialog component
ms.assetid: daf46e57-1b4b-4b7a-bad0-b50ca7ba75dc
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b1e00fc074148ddd53885bafbb490a3e3868fc0a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="fontdialog-component-overview-windows-forms"></a><span data-ttu-id="cfd30-102">FontDialog コンポーネントの概要 (Windows フォーム)</span><span class="sxs-lookup"><span data-stu-id="cfd30-102">FontDialog Component Overview (Windows Forms)</span></span>
<span data-ttu-id="cfd30-103">Windows フォーム<xref:System.Windows.Forms.FontDialog>コンポーネントは、構成済みのダイアログ ボックスは、これは、標準の Windows**フォント** ダイアログ ボックスを使用して、システムに現在インストールされているフォントを公開します。</span><span class="sxs-lookup"><span data-stu-id="cfd30-103">The Windows Forms <xref:System.Windows.Forms.FontDialog> component is a pre-configured dialog box, which is the standard Windows **Font** dialog box used to expose the fonts that are currently installed on the system.</span></span> <span data-ttu-id="cfd30-104">独自のダイアログ ボックスを構成する代わりにフォントの選択の簡単な解決策として、Windows ベースのアプリケーション内で使用します。</span><span class="sxs-lookup"><span data-stu-id="cfd30-104">Use it within your Windows-based application as a simple solution for font selection in lieu of configuring your own dialog box.</span></span>  
  
 <span data-ttu-id="cfd30-105">既定では、ダイアログ ボックスに表示リスト ボックスのフォント、フォント スタイル、およびサイズです。取り消し線、下線; などの効果のチェック ボックススクリプトのドロップダウン リストフォントがどのように表示されるかのサンプルです。</span><span class="sxs-lookup"><span data-stu-id="cfd30-105">By default, the dialog box shows list boxes for Font, Font style, and Size; check boxes for effects like Strikeout and Underline; a drop-down list for Script; and a sample of how the font will appear.</span></span> <span data-ttu-id="cfd30-106">(スクリプトは、特定のフォントで利用可能な異なる文字スクリプトなど、ヘブライ語や日本語)。表示するには、[フォント] ダイアログ ボックスを呼び出す、<xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="cfd30-106">(Script refers to different character scripts that are available for a given font, for example, Hebrew or Japanese.) To display the font dialog box, call the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="cfd30-107">主要プロパティ</span><span class="sxs-lookup"><span data-stu-id="cfd30-107">Key Properties</span></span>  
 <span data-ttu-id="cfd30-108">コンポーネントが、その外観を構成するプロパティの数。</span><span class="sxs-lookup"><span data-stu-id="cfd30-108">The component has a number of properties that configure its appearance.</span></span> <span data-ttu-id="cfd30-109">ダイアログ ボックスの選択項目を設定するプロパティは<xref:System.Windows.Forms.FontDialog.Font%2A>と<xref:System.Windows.Forms.FontDialog.Color%2A>です。</span><span class="sxs-lookup"><span data-stu-id="cfd30-109">The properties that set the dialog-box selections are <xref:System.Windows.Forms.FontDialog.Font%2A> and <xref:System.Windows.Forms.FontDialog.Color%2A>.</span></span> <span data-ttu-id="cfd30-110"><xref:System.Windows.Forms.FontDialog.Font%2A>プロパティ設定のフォント、スタイル、サイズ、スクリプト、および影響です。 たとえば、`Arial, 10pt, style=Italic, Strikeout`です。</span><span class="sxs-lookup"><span data-stu-id="cfd30-110">The <xref:System.Windows.Forms.FontDialog.Font%2A> property sets the font, style, size, script, and effects; for example, `Arial, 10pt, style=Italic, Strikeout`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfd30-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="cfd30-111">See Also</span></span>  
 <xref:System.Windows.Forms.FontDialog>  
 [<span data-ttu-id="cfd30-112">FontDialog コンポーネント</span><span class="sxs-lookup"><span data-stu-id="cfd30-112">FontDialog Component</span></span>](../../../../docs/framework/winforms/controls/fontdialog-component-windows-forms.md)
