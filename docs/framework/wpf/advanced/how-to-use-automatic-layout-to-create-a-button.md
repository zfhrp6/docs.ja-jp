---
title: '方法: 自動レイアウトを使用してボタンを作成する'
ms.date: 03/30/2017
helpviewer_keywords:
- Button controls [WPF], creating with automatic layout
- automatic layout [WPF], creating buttons
ms.assetid: 96c206d0-9e77-4784-9d2d-5045aed2021c
ms.openlocfilehash: 34b372e886b31e801b5598da90299f9815c47620
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545215"
---
# <a name="how-to-use-automatic-layout-to-create-a-button"></a><span data-ttu-id="24a2e-102">方法: 自動レイアウトを使用してボタンを作成する</span><span class="sxs-lookup"><span data-stu-id="24a2e-102">How to: Use Automatic Layout to Create a Button</span></span>
<span data-ttu-id="24a2e-103">この例では、自動レイアウトの方法を使用して、ローカライズ可能なアプリケーションにボタンを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="24a2e-103">This example describes how to use the automatic layout approach to create a button in a localizable application.</span></span>  
  
 <span data-ttu-id="24a2e-104">ローカライズ、[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]時間のかかるプロセスを指定できます。</span><span class="sxs-lookup"><span data-stu-id="24a2e-104">Localization of a [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] can be a time consuming process.</span></span> <span data-ttu-id="24a2e-105">多くの場合、ローカライザーは、テキストの翻訳だけでなく、要素のサイズ変更や位置変更を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="24a2e-105">Often localizers need to resize and reposition elements in addition to translating text.</span></span> <span data-ttu-id="24a2e-106">過去の各言語を[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]必要な調整が翻訳します。</span><span class="sxs-lookup"><span data-stu-id="24a2e-106">In the past each language that a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] was adapted for required adjustment.</span></span> <span data-ttu-id="24a2e-107">機能を持つようになりました[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]調整の必要性が軽減される要素を設計することができます。</span><span class="sxs-lookup"><span data-stu-id="24a2e-107">Now with the capabilities of [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] you can design elements that reduce the need for adjustment.</span></span> <span data-ttu-id="24a2e-108">簡単にサイズ変更や再配置できるアプリケーションの作成方法と呼びます`automatic layout`です。</span><span class="sxs-lookup"><span data-stu-id="24a2e-108">The approach to writing applications that can be more easily resized and repositioned is called `automatic layout`.</span></span>  
  
 <span data-ttu-id="24a2e-109">次の 2 つ[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]の例は、ボタン以外の場合は英語のテキストとスペイン語のテキストのインスタンスを作成するアプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="24a2e-109">The following two [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] examples create applications that instantiate a button; one with English text and one with Spanish text.</span></span> <span data-ttu-id="24a2e-110">テキストを除き、コードは同じであることに注目してください。ボタンがテキストに合わせて調整されます。</span><span class="sxs-lookup"><span data-stu-id="24a2e-110">Notice that the code is the same except for the text; the button adjusts to fit the text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="24a2e-111">例</span><span class="sxs-lookup"><span data-stu-id="24a2e-111">Example</span></span>  
 [!code-xaml[LocalizationBtn_snip#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn_snip/CS/Pane1.xaml#1)]  
  
 [!code-xaml[LocalizationBtn#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn/CS/Pane1.xaml#1)]  
  
 <span data-ttu-id="24a2e-112">次の図は、コード サンプルの出力を示しています。</span><span class="sxs-lookup"><span data-stu-id="24a2e-112">The following graphic shows the output of the code samples.</span></span>  
  
 <span data-ttu-id="24a2e-113">![同じテキストのボタンを異なる言語で](../../../../docs/framework/wpf/advanced/media/globalizationbutton.png "GlobalizationButton")</span><span class="sxs-lookup"><span data-stu-id="24a2e-113">![The same button with text in different languages](../../../../docs/framework/wpf/advanced/media/globalizationbutton.png "GlobalizationButton")</span></span>  
<span data-ttu-id="24a2e-114">自動サイズ変更可能なボタン</span><span class="sxs-lookup"><span data-stu-id="24a2e-114">Auto Resizable Button</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24a2e-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="24a2e-115">See Also</span></span>  
 [<span data-ttu-id="24a2e-116">自動レイアウトの使用の概要</span><span class="sxs-lookup"><span data-stu-id="24a2e-116">Use Automatic Layout Overview</span></span>](../../../../docs/framework/wpf/advanced/use-automatic-layout-overview.md)  
 [<span data-ttu-id="24a2e-117">自動レイアウト用のグリッドを使用する</span><span class="sxs-lookup"><span data-stu-id="24a2e-117">Use a Grid for Automatic Layout</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-a-grid-for-automatic-layout.md)
