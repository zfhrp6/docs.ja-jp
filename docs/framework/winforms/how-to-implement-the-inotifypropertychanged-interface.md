---
title: "方法 : INotifyPropertyChanged インターフェイスを実装する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- INotifyPropertyChanged interface [Windows Forms], implementing
ms.assetid: eac428af-b43b-46ac-80d9-1a5f88658725
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7ded5d11c9a9f93848e17c372e961f9f6a3b4226
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-implement-the-inotifypropertychanged-interface"></a><span data-ttu-id="cdc37-102">方法 : INotifyPropertyChanged インターフェイスを実装する</span><span class="sxs-lookup"><span data-stu-id="cdc37-102">How to: Implement the INotifyPropertyChanged Interface</span></span>
<span data-ttu-id="cdc37-103">次のコード例は、実装する方法を示します、<xref:System.ComponentModel.INotifyPropertyChanged>インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="cdc37-103">The following code example demonstrates how to implement the <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span></span> <span data-ttu-id="cdc37-104">Windows フォーム データ バインディングで使用されているビジネス オブジェクトでは、このインターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="cdc37-104">Implement this interface on business objects that are used in Windows Forms data binding.</span></span> <span data-ttu-id="cdc37-105">実装された場合、インターフェイスは、ビジネス オブジェクトでプロパティの変更をバインドされたコントロールを通信します。</span><span class="sxs-lookup"><span data-stu-id="cdc37-105">When implemented, the interface  communicates to a bound control the property changes on a business object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cdc37-106">例</span><span class="sxs-lookup"><span data-stu-id="cdc37-106">Example</span></span>  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="cdc37-107">参照</span><span class="sxs-lookup"><span data-stu-id="cdc37-107">See Also</span></span>  
 [<span data-ttu-id="cdc37-108">方法: PropertyNameChanged パターンを適用する</span><span class="sxs-lookup"><span data-stu-id="cdc37-108">How to: Apply the PropertyNameChanged Pattern</span></span>](../../../docs/framework/winforms/how-to-apply-the-propertynamechanged-pattern.md)  
 [<span data-ttu-id="cdc37-109">Windows フォームでのデータ バインディング</span><span class="sxs-lookup"><span data-stu-id="cdc37-109">Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [<span data-ttu-id="cdc37-110">方法: BindingSource と INotifyPropertyChanged の各インターフェイスを使用して変更通知を発生させる</span><span class="sxs-lookup"><span data-stu-id="cdc37-110">How to: Raise Change Notifications Using a BindingSource and the INotifyPropertyChanged Interface</span></span>](../../../docs/framework/winforms/controls/raise-change-notifications--bindingsource.md)  
 [<span data-ttu-id="cdc37-111">Windows フォーム データ バインドの変更通知</span><span class="sxs-lookup"><span data-stu-id="cdc37-111">Change Notification in Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)
