---
title: "方法 : Windows フォームでファイルに関連付けられているアイコンを抽出する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- displaying a file name and its file type icon in a ListView control [Windows Forms]
- file name extension icons [Windows Forms], displaying in a ListView
- extracting icons associated with a file type [Windows Forms]
ms.assetid: 88e2ad8b-c34f-415a-84f2-dad756b5c928
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a5153f6389c4477a18c647d7cdaf7b49b43bb7ca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-extract-the-icon-associated-with-a-file-in-windows-forms"></a><span data-ttu-id="f2e24-102">方法 : Windows フォームでファイルに関連付けられているアイコンを抽出する</span><span class="sxs-lookup"><span data-stu-id="f2e24-102">How to: Extract the Icon Associated with a File in Windows Forms</span></span>
<span data-ttu-id="f2e24-103">多くのファイルには、関連付けられているファイルの種類の視覚的に表示されるアイコンが埋め込まれています。</span><span class="sxs-lookup"><span data-stu-id="f2e24-103">Many files have embedded icons that provide a visual representation of the associated file type.</span></span> <span data-ttu-id="f2e24-104">たとえば、Microsoft Word ドキュメントには、Word 文書として識別されるアイコンが含まれます。</span><span class="sxs-lookup"><span data-stu-id="f2e24-104">For example, Microsoft Word documents contain an icon that identifies them as Word documents.</span></span> <span data-ttu-id="f2e24-105">ファイルを表示する、テーブル コントロールまたはリスト コントロールで、ときに各ファイル名の横にあるファイルの種類を表すアイコンを表示することがあります。</span><span class="sxs-lookup"><span data-stu-id="f2e24-105">When displaying files in a list control or table control, you may want to display the icon representing the file type next to each file name.</span></span> <span data-ttu-id="f2e24-106">使用して簡単に行うことができます、<xref:System.Drawing.Icon.ExtractAssociatedIcon%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="f2e24-106">You can do this easily by using the <xref:System.Drawing.Icon.ExtractAssociatedIcon%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f2e24-107">例</span><span class="sxs-lookup"><span data-stu-id="f2e24-107">Example</span></span>  
 <span data-ttu-id="f2e24-108">次のコード例をファイルに関連付けられたアイコンを抽出して、ファイル名と関連付けられているアイコンで表示する方法を示しています、<xref:System.Windows.Forms.ListView>コントロール。</span><span class="sxs-lookup"><span data-stu-id="f2e24-108">The following code example demonstrates how to extract the icon associated with a file and display the file name and its associated icon in a <xref:System.Windows.Forms.ListView> control.</span></span>  
  
 [!code-csharp[System.Drawing.Icon.ExtractAssociatedIconEx#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Icon.ExtractAssociatedIconEx/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Icon.ExtractAssociatedIconEx#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Icon.ExtractAssociatedIconEx/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f2e24-109">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="f2e24-109">Compiling the Code</span></span>  
 <span data-ttu-id="f2e24-110">例をコンパイルするには。</span><span class="sxs-lookup"><span data-stu-id="f2e24-110">To compile the example:</span></span>  
  
-   <span data-ttu-id="f2e24-111">Windows フォームと呼び出しに上記のコードを貼り付けます、`ExtractAssociatedIconExample`フォームのコンス トラクターからのメソッドまたは<xref:System.Windows.Forms.Form.Load>イベント処理メソッドです。</span><span class="sxs-lookup"><span data-stu-id="f2e24-111">Paste the preceding code into a Windows Form, and call the `ExtractAssociatedIconExample` method from the form's constructor or <xref:System.Windows.Forms.Form.Load> event-handling method.</span></span>  
  
     <span data-ttu-id="f2e24-112">フォームをインポートすることを確認する必要があります、<xref:System.IO>名前空間。</span><span class="sxs-lookup"><span data-stu-id="f2e24-112">You will need to make sure that your form imports the <xref:System.IO> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2e24-113">参照</span><span class="sxs-lookup"><span data-stu-id="f2e24-113">See Also</span></span>  
 [<span data-ttu-id="f2e24-114">イメージ、ビットマップ、メタファイル</span><span class="sxs-lookup"><span data-stu-id="f2e24-114">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [<span data-ttu-id="f2e24-115">ListView コントロール</span><span class="sxs-lookup"><span data-stu-id="f2e24-115">ListView Control</span></span>](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)
