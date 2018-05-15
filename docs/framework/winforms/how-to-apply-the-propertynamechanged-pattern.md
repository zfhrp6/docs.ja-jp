---
title: '方法 : PropertyNameChanged パターンを適用する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], property changes (using code)
- data binding [Windows Forms], custom controls
- PropertyNameChanged pattern [Windows Forms], applying
ms.assetid: aa47ddf6-5223-40c4-833f-a78992194836
ms.openlocfilehash: 775a27b1b4ba8143e297a3c4d323356a304073a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-apply-the-propertynamechanged-pattern"></a><span data-ttu-id="e0cb3-102">方法 : PropertyNameChanged パターンを適用する</span><span class="sxs-lookup"><span data-stu-id="e0cb3-102">How to: Apply the PropertyNameChanged Pattern</span></span>
<span data-ttu-id="e0cb3-103">次のコード例を適用する方法を示しています、 *PropertyName*Changed パターンをカスタム コントロールです。</span><span class="sxs-lookup"><span data-stu-id="e0cb3-103">The following code example demonstrates how to apply the *PropertyName*Changed pattern to a custom control.</span></span> <span data-ttu-id="e0cb3-104">Windows フォーム データ バインディング エンジンで使用されるカスタム コントロールを実装する場合は、このパターンを適用します。</span><span class="sxs-lookup"><span data-stu-id="e0cb3-104">Apply this pattern when you implement custom controls that are used with the Windows Forms data binding engine.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0cb3-105">例</span><span class="sxs-lookup"><span data-stu-id="e0cb3-105">Example</span></span>  
 [!code-csharp[System.Windows.Forms.ChangeNotification#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ChangeNotification/CS/Form1.cs#3)]
 [!code-vb[System.Windows.Forms.ChangeNotification#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ChangeNotification/VB/Form1.vb#3)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e0cb3-106">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="e0cb3-106">Compiling the Code</span></span>  
 <span data-ttu-id="e0cb3-107">上記のコード例をコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="e0cb3-107">To compile the previous code example:</span></span>  
  
-   <span data-ttu-id="e0cb3-108">空のコード ファイルにコードを貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="e0cb3-108">Paste the code into an empty code file.</span></span> <span data-ttu-id="e0cb3-109">含む Windows フォームでのカスタム コントロールを使用する必要があります、`Main`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="e0cb3-109">You must use the custom control on a Windows Form that contains a `Main` method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0cb3-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="e0cb3-110">See Also</span></span>  
 [<span data-ttu-id="e0cb3-111">方法: INotifyPropertyChanged インターフェイスを実装する</span><span class="sxs-lookup"><span data-stu-id="e0cb3-111">How to: Implement the INotifyPropertyChanged Interface</span></span>](../../../docs/framework/winforms/how-to-implement-the-inotifypropertychanged-interface.md)  
 [<span data-ttu-id="e0cb3-112">Windows フォーム データ バインドの変更通知</span><span class="sxs-lookup"><span data-stu-id="e0cb3-112">Change Notification in Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)  
 [<span data-ttu-id="e0cb3-113">Windows フォームでのデータ バインディング</span><span class="sxs-lookup"><span data-stu-id="e0cb3-113">Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/windows-forms-data-binding.md)
