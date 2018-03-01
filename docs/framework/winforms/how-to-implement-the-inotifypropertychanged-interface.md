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
# <a name="how-to-implement-the-inotifypropertychanged-interface"></a>方法 : INotifyPropertyChanged インターフェイスを実装する
次のコード例は、実装する方法を示します、<xref:System.ComponentModel.INotifyPropertyChanged>インターフェイスです。 Windows フォーム データ バインディングで使用されているビジネス オブジェクトでは、このインターフェイスを実装します。 実装された場合、インターフェイスは、ビジネス オブジェクトでプロパティの変更をバインドされたコントロールを通信します。  
  
## <a name="example"></a>例  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>参照  
 [方法: PropertyNameChanged パターンを適用する](../../../docs/framework/winforms/how-to-apply-the-propertynamechanged-pattern.md)  
 [Windows フォームでのデータ バインディング](../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [方法: BindingSource と INotifyPropertyChanged の各インターフェイスを使用して変更通知を発生させる](../../../docs/framework/winforms/controls/raise-change-notifications--bindingsource.md)  
 [Windows フォーム データ バインドの変更通知](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)
