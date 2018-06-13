---
title: '方法 : Windows フォームを印刷する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, printing
- printing [Windows Forms]
- printing a form
- printing [Windows Forms], printing a form
ms.assetid: c8dff5f8-f56a-4c07-ae31-64643b31f8fc
ms.openlocfilehash: 42940654a0754ac3616ca7983af07d20607f480f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522270"
---
# <a name="how-to-print-a-windows-form"></a><span data-ttu-id="3c775-102">方法 : Windows フォームを印刷する</span><span class="sxs-lookup"><span data-stu-id="3c775-102">How to: Print a Windows Form</span></span>
<span data-ttu-id="3c775-103">開発プロセスの一環として、通常はする、Windows フォームのコピーを印刷します。</span><span class="sxs-lookup"><span data-stu-id="3c775-103">As part of the development process, you typically will want to print a copy of your Windows Form.</span></span> <span data-ttu-id="3c775-104">次のコード例を使用して現在のフォームのコピーを印刷する方法を示しています、<xref:System.Drawing.Graphics.CopyFromScreen%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="3c775-104">The following code example shows how to print a copy of the current form by using the <xref:System.Drawing.Graphics.CopyFromScreen%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3c775-105">例</span><span class="sxs-lookup"><span data-stu-id="3c775-105">Example</span></span>  
 [!code-csharp[System.Drawing.Graphics.CopyFromScreen#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Graphics.CopyFromScreen#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3c775-106">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="3c775-106">Compiling the Code</span></span>  
 <span data-ttu-id="3c775-107">これは、完全なコード例を含む、`Main`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="3c775-107">This is a complete code example that contains a `Main` method.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="3c775-108">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="3c775-108">Robust Programming</span></span>  
 <span data-ttu-id="3c775-109">次の条件を満たす場合は、例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3c775-109">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="3c775-110">プリンターへのアクセス許可がありません。</span><span class="sxs-lookup"><span data-stu-id="3c775-110">You do not have permission to access the printer.</span></span>  
  
-   <span data-ttu-id="3c775-111">プリンターをインストールすることはありません。</span><span class="sxs-lookup"><span data-stu-id="3c775-111">There is no printer installed.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="3c775-112">.NET Framework セキュリティ</span><span class="sxs-lookup"><span data-stu-id="3c775-112">.NET Framework Security</span></span>  
 <span data-ttu-id="3c775-113">このコード例を実行するためには、コンピューターで使用するプリンターにアクセスする権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="3c775-113">In order to run this code example, you must have permission to access the printer you use with your computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c775-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="3c775-114">See Also</span></span>  
 <xref:System.Drawing.Printing.PrintDocument>  
 [<span data-ttu-id="3c775-115">方法: GDI+ を使用してイメージをレンダリングする</span><span class="sxs-lookup"><span data-stu-id="3c775-115">How to: Render Images with GDI+</span></span>](../../../../docs/framework/winforms/advanced/how-to-render-images-with-gdi.md)  
 [<span data-ttu-id="3c775-116">方法: Windows フォームでグラフィックスを印刷する</span><span class="sxs-lookup"><span data-stu-id="3c775-116">How to: Print Graphics in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-print-graphics-in-windows-forms.md)
