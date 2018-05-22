---
title: '方法: XAML で特殊文字を使用する'
ms.date: 03/30/2017
helpviewer_keywords:
- Unicode UTF-8 file format
- UTF-8 file format
- characters [WPF], special
- typography [WPF], special characters
- special characters [WPF]
ms.assetid: a57776d1-f353-4794-afa0-bfa3c712ed1c
ms.openlocfilehash: c593ca094487e8f7016b02870026321fbcb9a7c3
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
---
# <a name="how-to-use-special-characters-in-xaml"></a><span data-ttu-id="f80a8-102">方法: XAML で特殊文字を使用する</span><span class="sxs-lookup"><span data-stu-id="f80a8-102">How to: Use Special Characters in XAML</span></span>
<span data-ttu-id="f80a8-103">マークアップ ファイル内に作成される[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]で自動的に保存、 [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] utf-8 ファイル形式は、アクセント記号などのほとんどの特殊文字を正しくエンコードすることを意味します。</span><span class="sxs-lookup"><span data-stu-id="f80a8-103">Markup files that are created in [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] are automatically saved in the [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] UTF-8 file format, which means that most special characters, such as accent marks, are encoded correctly.</span></span> <span data-ttu-id="f80a8-104">ただし、一般的に使用される一連の特殊文字で、別の方法で処理されるものがあります。</span><span class="sxs-lookup"><span data-stu-id="f80a8-104">However, there is a set of commonly-used special characters that are handled differently.</span></span> <span data-ttu-id="f80a8-105">これらの特殊文字に従って、 [!INCLUDE[TLA#tla_w3c](../../../../includes/tlasharptla-w3c-md.md)] [!INCLUDE[TL A#tla_xml](../../../../includes/tlasharptla-xml-md.md)]のエンコード標準です。</span><span class="sxs-lookup"><span data-stu-id="f80a8-105">These special characters follow the [!INCLUDE[TLA#tla_w3c](../../../../includes/tlasharptla-w3c-md.md)] [!INCLUDE[TL A#tla_xml](../../../../includes/tlasharptla-xml-md.md)] standard for encoding.</span></span>  
  
 <span data-ttu-id="f80a8-106">この一連の特殊文字をエンコードするための構文を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="f80a8-106">The following table shows the syntax for encoding this set of special characters:</span></span>  
  
|<span data-ttu-id="f80a8-107">文字</span><span class="sxs-lookup"><span data-stu-id="f80a8-107">Character</span></span>|<span data-ttu-id="f80a8-108">構文</span><span class="sxs-lookup"><span data-stu-id="f80a8-108">Syntax</span></span>|<span data-ttu-id="f80a8-109">説明</span><span class="sxs-lookup"><span data-stu-id="f80a8-109">Description</span></span>|  
|---------------|------------|-----------------|  
|<|`&lt;`|<span data-ttu-id="f80a8-110">より小さい記号</span><span class="sxs-lookup"><span data-stu-id="f80a8-110">Less than symbol.</span></span>|  
|>|`&gt;`|<span data-ttu-id="f80a8-111">より大きい記号</span><span class="sxs-lookup"><span data-stu-id="f80a8-111">Greater than sign.</span></span>|  
|&|`&amp;`|<span data-ttu-id="f80a8-112">アンパサンド記号</span><span class="sxs-lookup"><span data-stu-id="f80a8-112">Ampersand symbol.</span></span>|  
|<span data-ttu-id="f80a8-113">"</span><span class="sxs-lookup"><span data-stu-id="f80a8-113">"</span></span>|`&quot;`|<span data-ttu-id="f80a8-114">二重引用符記号</span><span class="sxs-lookup"><span data-stu-id="f80a8-114">Double quote symbol.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="f80a8-115">作成する場合、テキストを使用するマークアップ ファイル エディターなど[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]メモ帳でファイルを保存する必要があります、[!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)]は保持するために utf-8 ファイル形式は、特殊文字をエンコードします。</span><span class="sxs-lookup"><span data-stu-id="f80a8-115">If you create a markup file using a text editor, such as [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] Notepad, you must save the file in the [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] UTF-8 file format in order to preserve any encoded special characters.</span></span>  
  
 <span data-ttu-id="f80a8-116">次の例では、マークアップを作成するときにテキストで特殊文字を使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f80a8-116">The following example shows how you can use special characters in text when creating markup.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f80a8-117">例</span><span class="sxs-lookup"><span data-stu-id="f80a8-117">Example</span></span>  
 [!code-xaml[SpecialCharsSnippets#SpecialCharsSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpecialCharsSnippets/CS/Window1.xaml#specialcharssnippet1)]
