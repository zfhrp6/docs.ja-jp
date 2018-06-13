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
ms.locfileid: "33536747"
---
# <a name="how-to-apply-the-propertynamechanged-pattern"></a>方法 : PropertyNameChanged パターンを適用する
次のコード例を適用する方法を示しています、 *PropertyName*Changed パターンをカスタム コントロールです。 Windows フォーム データ バインディング エンジンで使用されるカスタム コントロールを実装する場合は、このパターンを適用します。  
  
## <a name="example"></a>例  
 [!code-csharp[System.Windows.Forms.ChangeNotification#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ChangeNotification/CS/Form1.cs#3)]
 [!code-vb[System.Windows.Forms.ChangeNotification#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ChangeNotification/VB/Form1.vb#3)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 上記のコード例をコンパイルします。  
  
-   空のコード ファイルにコードを貼り付けます。 含む Windows フォームでのカスタム コントロールを使用する必要があります、`Main`メソッドです。  
  
## <a name="see-also"></a>関連項目  
 [方法: INotifyPropertyChanged インターフェイスを実装する](../../../docs/framework/winforms/how-to-implement-the-inotifypropertychanged-interface.md)  
 [Windows フォーム データ バインドの変更通知](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)  
 [Windows フォームでのデータ バインディング](../../../docs/framework/winforms/windows-forms-data-binding.md)
