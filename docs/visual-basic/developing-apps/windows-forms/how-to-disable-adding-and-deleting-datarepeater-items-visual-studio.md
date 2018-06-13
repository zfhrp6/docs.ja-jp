---
title: '方法 : DataRepeater の項目の追加と削除を無効にする (Visual Studio)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, disabling delete
- DataRepeater, disabling add
ms.assetid: 298d8f60-ddfe-4361-ab66-cf76d0df5220
ms.openlocfilehash: e3d0d2a8d422054e269ee92df1fdfcb5acb96eac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590810"
---
# <a name="how-to-disable-adding-and-deleting-datarepeater-items-visual-studio"></a>方法 : DataRepeater の項目の追加と削除を無効にする (Visual Studio)
既定では、ユーザーは追加し、項目の削除、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール。 ユーザーは、CTRL キーを押しながら N キーを押して、新しい項目を追加できるときに、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A>にフォーカスがあるかをクリックして、 **AddNewItem**のボタンでは、<xref:System.Windows.Forms.BindingNavigator>コントロール。 ユーザーがキーを押して、項目を削除できるときに削除、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A>にフォーカスがあるかをクリックして、 **DeleteItem**のボタンでは、<xref:System.Windows.Forms.BindingNavigator>コントロール。  
  
 追加と削除のデザイン時または実行時に無効にすることができます。  
  
### <a name="to-disable-adding-and-deleting-at-design-time"></a>デザイン時に追加と削除を無効にするには  
  
1.  Windows フォーム デザイナーで、選択、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール。  
  
    > [!NOTE]
    >  コントロールの下のセクションを選択する必要があります。 項目テンプレートのセクションを選択すると、異なる一連のプロパティが表示されます。  
  
2.  [プロパティ] ウィンドウで、設定、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToAddItems%2A>プロパティを**False**です。  
  
3.  設定、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToDeleteItems%2A>プロパティを**False**です。  
  
4.  Windows フォーム デザイナーで、選択、<xref:System.Windows.Forms.BindingNavigator>コントロールをクリックして、 **AddNewItem**ボタン (に正符号のボタン)。  
  
5.  [プロパティ] ウィンドウで、設定、<xref:System.Windows.Forms.ToolBarButton.Enabled%2A>プロパティを**False**です。  
  
6.  Windows フォーム デザイナーで、選択、<xref:System.Windows.Forms.BindingNavigator>コントロールをクリックして、 **DeleteItem** (に赤い x 印が付いたボタン) のボタンをクリックします。  
  
7.  [プロパティ] ウィンドウで、設定、<xref:System.Windows.Forms.ToolBarButton.Enabled%2A>プロパティを**False**です。  
  
8.  コンポーネント トレイに次のように選択します。、<xref:System.Windows.Forms.BindingSource>先、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>がバインドされています。  
  
9. [プロパティ] ウィンドウで、設定、<xref:System.Windows.Forms.BindingSource.AllowNew%2A>プロパティを**False**です。  
  
10. Windows フォーム デザイナーで、ダブルクリック、 **DeleteItem**ボタン コード エディターを開きます。  
  
11. イベント ドロップダウン リストで、選択、`BindingNavigatorDeleteItem_EnabledChanged`イベント。  
  
12. `BindingNavigatorDeleteItem_EnabledChanged` イベント ハンドラーに次のコードを追加します。  
  
     [!code-csharp[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.vb)]  
  
    > [!NOTE]
    >  この手順が必要なのは、現在のレコードが変更されるたびに <xref:System.Windows.Forms.BindingSource> によって **DeleteItem** ボタンが有効になるためです。  
  
### <a name="to-disable-adding-and-deleting-at-run-time"></a>実行時に追加と削除を無効にするには  
  
1.  Windows フォーム デザイナーで、フォームをダブルクリックしてコード エディターを開きます。  
  
2.  `Form_Load` イベントに次のコードを追加します。  
  
     [!code-csharp[VbPowerPacksDataRepeaterDisableAddDelete#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_2.cs)]
     [!code-vb[VbPowerPacksDataRepeaterDisableAddDelete#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_2.vb)]  
  
3.  `BindingNavigatorDeleteItem_EnabledChanged` イベント ハンドラーに次のコードを追加します。  
  
     [!code-csharp[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.vb)]  
  
    > [!NOTE]
    >  この手順が必要なのは、現在のレコードが変更されるたびに <xref:System.Windows.Forms.BindingSource> によって **DeleteItem** ボタンが有効になるためです。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [DataRepeater コントロールの概要](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [DataRepeater コントロールのトラブルシューティング](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
