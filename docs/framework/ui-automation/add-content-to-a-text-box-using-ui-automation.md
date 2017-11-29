---
title: "UI オートメーションを使用した、テキスト ボックスへのコンテンツの追加"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adding content to text boxes
- text boxes, adding content
- UI Automation, adding content to text boxes
ms.assetid: 8bdd1a73-1ecb-4a05-a891-a7827ebb767f
caps.latest.revision: "13"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 0acd6510e6349917b38e33e487123a118c2e653c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="add-content-to-a-text-box-using-ui-automation"></a><span data-ttu-id="b2076-102">UI オートメーションを使用した、テキスト ボックスへのコンテンツの追加</span><span class="sxs-lookup"><span data-stu-id="b2076-102">Add Content to a Text Box Using UI Automation</span></span>
> [!NOTE]
>  <span data-ttu-id="b2076-103">このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージ <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="b2076-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="b2076-104">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI Automation (Windows のオートメーション API: UI オートメーション)](http://go.microsoft.com/fwlink/?LinkID=156746)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b2076-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="b2076-105">このトピックを使用する方法を示すコード例が含まれています。[!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]単一行のテキスト ボックスにテキストを挿入します。</span><span class="sxs-lookup"><span data-stu-id="b2076-105">This topic contains example code that demonstrates how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to insert text into a single-line text box.</span></span> <span data-ttu-id="b2076-106">複数行およびリッチ テキスト コントロールを別の方法が提供される、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]は適用されません。</span><span class="sxs-lookup"><span data-stu-id="b2076-106">An alternate method is provided for multi-line and rich text controls where [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] is not applicable.</span></span> <span data-ttu-id="b2076-107">例は、比較のための Win32 メソッドを使用して、同じ結果を達成する方法も示します。</span><span class="sxs-lookup"><span data-stu-id="b2076-107">For comparison purposes, the example also demonstrates how to use Win32 methods to accomplish the same results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b2076-108">例</span><span class="sxs-lookup"><span data-stu-id="b2076-108">Example</span></span>  
 <span data-ttu-id="b2076-109">ターゲット アプリケーション内のテキスト コントロールのシーケンスで次の例の手順です。</span><span class="sxs-lookup"><span data-stu-id="b2076-109">The following example steps through a sequence of text controls in a target application.</span></span> <span data-ttu-id="b2076-110">各テキスト コントロールがかどうかをテストする<xref:System.Windows.Automation.ValuePattern>オブジェクトを取得するにを使用して、<xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="b2076-110">Each text control is tested to see if a <xref:System.Windows.Automation.ValuePattern> object can be obtained from it using the <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> method.</span></span> <span data-ttu-id="b2076-111">場合は、テキスト コントロールはサポート<xref:System.Windows.Automation.ValuePattern>、<xref:System.Windows.Automation.ValuePattern.SetValue%2A>テキスト コントロールにユーザー定義の文字列を挿入するメソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="b2076-111">If the text control does support <xref:System.Windows.Automation.ValuePattern>, the <xref:System.Windows.Automation.ValuePattern.SetValue%2A> method is used to insert a user-defined string into the text control.</span></span> <span data-ttu-id="b2076-112">それ以外の場合、<xref:System.Windows.Forms.SendKeys.SendWait%2A?displayProperty=nameWithType>メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="b2076-112">Otherwise, the <xref:System.Windows.Forms.SendKeys.SendWait%2A?displayProperty=nameWithType> method is used.</span></span>  
  
 [!code-csharp[InsertText#InsertText](../../../samples/snippets/csharp/VS_Snippets_Wpf/InsertText/CSharp/Window1.xaml.cs#inserttext)]
 [!code-vb[InsertText#InsertText](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InsertText/VisualBasic/Window1.xaml.vb#inserttext)]  
  
## <a name="see-also"></a><span data-ttu-id="b2076-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="b2076-113">See Also</span></span>  
 [<span data-ttu-id="b2076-114">TextPattern の挿入テキスト サンプル</span><span class="sxs-lookup"><span data-stu-id="b2076-114">TextPattern Insert Text Sample</span></span>](http://msdn.microsoft.com/en-us/67353f93-7ee2-42f2-ab76-5c078cf6ca16)
