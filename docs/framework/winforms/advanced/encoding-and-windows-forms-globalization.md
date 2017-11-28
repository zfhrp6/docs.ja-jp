---
title: "エンコード方式および Windows フォームのグローバリゼーション"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ListView control [Windows Forms], lack of Unicode support
- DateTimePicker control [Windows Forms], lack of Unicode support
- TrackBar control [Windows Forms], lack of Unicode support
- ImageList component [Windows Forms], lack of Unicode support
- Unicode [Windows Forms]
- ToolBar control [Windows Forms], lack of Unicode support
- international applications [Windows Forms], character display
- StatusBar control [Windows Forms], lack of Unicode support
- MonthCalendar control [Windows Forms], lack of Unicode support
- international characters
- TabControl control [Windows Forms], lack of Unicode support
- Windows Forms, encoding
- TreeView control [Windows Forms], lack of Unicode support
- ProgressBar control [Windows Forms], Unicode-enabled forms
- localization [Windows Forms], character sets
- globalization [Windows Forms], character sets
ms.assetid: 22e8965d-a712-42b3-8167-3ee346bd70f9
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cbac07e92d892913f2d2a342b2fa5b3d5fe2f40c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="encoding-and-windows-forms-globalization"></a><span data-ttu-id="cdfe2-102">エンコード方式および Windows フォームのグローバリゼーション</span><span class="sxs-lookup"><span data-stu-id="cdfe2-102">Encoding and Windows Forms Globalization</span></span>
<span data-ttu-id="cdfe2-103">Windows フォーム アプリケーションは、Unicode に完全対応しているため、プラットフォーム、プログラム、または言語に関係なく、文字がそれぞれ一意の数字で表されます。</span><span class="sxs-lookup"><span data-stu-id="cdfe2-103">Windows Forms applications are entirely Unicode-enabled, meaning that each character is represented by a unique number, no matter what the platform, program, or language.</span></span> <span data-ttu-id="cdfe2-104">Unicode の詳細については、次を参照してください。、 [Unicode コンソーシアムの Web サイト](http://www.unicode.org)です。</span><span class="sxs-lookup"><span data-stu-id="cdfe2-104">For more information about Unicode, see the [Unicode consortium Web site](http://www.unicode.org).</span></span>  
  
## <a name="benefits-of-unicode"></a><span data-ttu-id="cdfe2-105">Unicode の利点</span><span class="sxs-lookup"><span data-stu-id="cdfe2-105">Benefits of Unicode</span></span>  
 <span data-ttu-id="cdfe2-106">Unicode 対応フォームの利点として、ヒンディー語などの Unicode 専用のスクリプトを操作できる点も含まれます。</span><span class="sxs-lookup"><span data-stu-id="cdfe2-106">The benefits of Unicode-enabled forms include the ability to work with scripts that are Unicode-only, such as Hindi.</span></span> <span data-ttu-id="cdfe2-107">さらに、1 つのフォームで複数の言語を使用できます。</span><span class="sxs-lookup"><span data-stu-id="cdfe2-107">In addition, you can use multiple languages on a single form.</span></span> <span data-ttu-id="cdfe2-108">Unicode では、すべての文字が 2 バイト長なので、2 バイト文字を表すために特別な作業は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="cdfe2-108">In Unicode, all characters are two bytes long, so no special effort is needed to represent double-byte characters.</span></span> <span data-ttu-id="cdfe2-109">また、すべてのプラットフォームで動作する 1 つのコードのセットを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="cdfe2-109">You can also write a single set of code that will work on all platforms.</span></span> <span data-ttu-id="cdfe2-110">これは、Windows NT や [!INCLUDE[win98](../../../../includes/win98-md.md)] など、プラットフォームが異なると別のコードを作成する必要がある、以前のバージョンの [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] から変更されています。</span><span class="sxs-lookup"><span data-stu-id="cdfe2-110">This is a change from previous versions of [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], in which you had to write different code for different platforms, such as Windows NT and [!INCLUDE[win98](../../../../includes/win98-md.md)].</span></span>  
  
 <span data-ttu-id="cdfe2-111">ただし、[!INCLUDE[win98](../../../../includes/win98-md.md)] および Windows Millennium Edition では、特定のコントロールが Unicode をサポートしません。</span><span class="sxs-lookup"><span data-stu-id="cdfe2-111">However, certain controls do not support Unicode in [!INCLUDE[win98](../../../../includes/win98-md.md)] and Windows Millennium Edition.</span></span> <span data-ttu-id="cdfe2-112">これらのコントロールはすべてコモン コントロールから継承されていて、Windows コード ページで [!INCLUDE[vcpransi](../../../../includes/vcpransi-md.md)] としてデータを処理します。</span><span class="sxs-lookup"><span data-stu-id="cdfe2-112">These controls, all of which inherit from the common control, will process data with the Windows code pages, as [!INCLUDE[vcpransi](../../../../includes/vcpransi-md.md)].</span></span> <span data-ttu-id="cdfe2-113">これらのコントロールは、<xref:System.Windows.Forms.TabControl>、<xref:System.Windows.Forms.ListView>、<xref:System.Windows.Forms.TreeView>、<xref:System.Windows.Forms.DateTimePicker>、<xref:System.Windows.Forms.MonthCalendar>、<xref:System.Windows.Forms.TrackBar>、<xref:System.Windows.Forms.ProgressBar>、<xref:System.Windows.Forms.ImageList>、<xref:System.Windows.Forms.ToolBar>、および <xref:System.Windows.Forms.StatusBar> です。</span><span class="sxs-lookup"><span data-stu-id="cdfe2-113">These controls are: <xref:System.Windows.Forms.TabControl>, <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.DateTimePicker>, <xref:System.Windows.Forms.MonthCalendar>, <xref:System.Windows.Forms.TrackBar>, <xref:System.Windows.Forms.ProgressBar>, <xref:System.Windows.Forms.ImageList>, <xref:System.Windows.Forms.ToolBar>, and <xref:System.Windows.Forms.StatusBar>.</span></span> <span data-ttu-id="cdfe2-114">その結果、前述のプラットフォーム上のこれらのコントロールで Unicode データを表示することはできません。</span><span class="sxs-lookup"><span data-stu-id="cdfe2-114">As a result, you cannot display Unicode data in these controls on the listed platforms.</span></span> <span data-ttu-id="cdfe2-115">たとえば、日本語の文字を英語の [!INCLUDE[win98](../../../../includes/win98-md.md)] オペレーティング システムで表示することはできません。</span><span class="sxs-lookup"><span data-stu-id="cdfe2-115">For example, you cannot display Japanese characters on an English [!INCLUDE[win98](../../../../includes/win98-md.md)] operating system.</span></span>  
  
 <span data-ttu-id="cdfe2-116"><xref:System.Windows.Forms.ToolBar> コントロールと <xref:System.Windows.Forms.StatusBar> コントロールの Unicode 対応の代替手段として、これらの古いコントロールを置換する <xref:System.Windows.Forms.ToolStrip> コントロールと <xref:System.Windows.Forms.StatusStrip> コントロールを使用します。</span><span class="sxs-lookup"><span data-stu-id="cdfe2-116">For Unicode-aware alternatives to the <xref:System.Windows.Forms.ToolBar> and <xref:System.Windows.Forms.StatusBar> controls, use the <xref:System.Windows.Forms.ToolStrip> and <xref:System.Windows.Forms.StatusStrip> controls, which replace these older controls.</span></span> <span data-ttu-id="cdfe2-117">アプリケーションの視覚要素の間で同様のルック アンド フィールを維持するには、メニューの表示に <xref:System.Windows.Forms.MainMenu> の代わりに <xref:System.Windows.Forms.MenuStrip> コントロールを使用します。</span><span class="sxs-lookup"><span data-stu-id="cdfe2-117">To maintain a similar look and feel between visual elements in your application, use the <xref:System.Windows.Forms.MenuStrip> control for rendering menus instead of <xref:System.Windows.Forms.MainMenu>.</span></span> <span data-ttu-id="cdfe2-118"><xref:System.Windows.Forms.ToolStrip> と <xref:System.Windows.Forms.StatusStrip> のように、<xref:System.Windows.Forms.MenuStrip> も Unicode 文字を処理して表示することができます。</span><span class="sxs-lookup"><span data-stu-id="cdfe2-118">Like <xref:System.Windows.Forms.ToolStrip> and <xref:System.Windows.Forms.StatusStrip>, <xref:System.Windows.Forms.MenuStrip> can also process and display Unicode characters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdfe2-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="cdfe2-119">See Also</span></span>  
 [<span data-ttu-id="cdfe2-120">Windows フォームのグローバル化</span><span class="sxs-lookup"><span data-stu-id="cdfe2-120">Globalizing Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/globalizing-windows-forms.md)
