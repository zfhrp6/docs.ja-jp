---
title: "方法 : PropertyNameChanged パターンを適用する"
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
- custom controls [Windows Forms], property changes (using code)
- data binding [Windows Forms], custom controls
- PropertyNameChanged pattern [Windows Forms], applying
ms.assetid: aa47ddf6-5223-40c4-833f-a78992194836
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4f53dd2fdaa622e022f49c153b6dbc83030ae791
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-apply-the-propertynamechanged-pattern"></a><span data-ttu-id="552d1-102">方法 : PropertyNameChanged パターンを適用する</span><span class="sxs-lookup"><span data-stu-id="552d1-102">How to: Apply the PropertyNameChanged Pattern</span></span>
<span data-ttu-id="552d1-103">次のコード例を適用する方法を示しています、 *PropertyName*Changed パターンをカスタム コントロールです。</span><span class="sxs-lookup"><span data-stu-id="552d1-103">The following code example demonstrates how to apply the *PropertyName*Changed pattern to a custom control.</span></span> <span data-ttu-id="552d1-104">Windows フォーム データ バインディング エンジンで使用されるカスタム コントロールを実装する場合は、このパターンを適用します。</span><span class="sxs-lookup"><span data-stu-id="552d1-104">Apply this pattern when you implement custom controls that are used with the Windows Forms data binding engine.</span></span>  
  
## <a name="example"></a><span data-ttu-id="552d1-105">例</span><span class="sxs-lookup"><span data-stu-id="552d1-105">Example</span></span>  
 [!code-csharp[System.Windows.Forms.ChangeNotification#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ChangeNotification/CS/Form1.cs#3)]
 [!code-vb[System.Windows.Forms.ChangeNotification#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ChangeNotification/VB/Form1.vb#3)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="552d1-106">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="552d1-106">Compiling the Code</span></span>  
 <span data-ttu-id="552d1-107">上記のコード例をコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="552d1-107">To compile the previous code example:</span></span>  
  
-   <span data-ttu-id="552d1-108">空のコード ファイルにコードを貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="552d1-108">Paste the code into an empty code file.</span></span> <span data-ttu-id="552d1-109">含む Windows フォームでのカスタム コントロールを使用する必要があります、`Main`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="552d1-109">You must use the custom control on a Windows Form that contains a `Main` method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="552d1-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="552d1-110">See Also</span></span>  
 [<span data-ttu-id="552d1-111">方法: INotifyPropertyChanged インターフェイスを実装する</span><span class="sxs-lookup"><span data-stu-id="552d1-111">How to: Implement the INotifyPropertyChanged Interface</span></span>](../../../docs/framework/winforms/how-to-implement-the-inotifypropertychanged-interface.md)  
 [<span data-ttu-id="552d1-112">Windows フォーム データ バインドの変更通知</span><span class="sxs-lookup"><span data-stu-id="552d1-112">Change Notification in Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)  
 [<span data-ttu-id="552d1-113">Windows フォームでのデータ バインディング</span><span class="sxs-lookup"><span data-stu-id="552d1-113">Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/windows-forms-data-binding.md)
