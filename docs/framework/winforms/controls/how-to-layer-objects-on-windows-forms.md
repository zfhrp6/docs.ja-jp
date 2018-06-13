---
title: '方法 : Windows フォーム上のオブジェクトをレイヤー化する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, layering
- controls [Windows Forms], layering
- z order
- controls [Windows Forms], positioning
- z-order
ms.assetid: 1acc4281-2976-4715-86f4-bda68134baaf
ms.openlocfilehash: 1a2a25f2e7eaa6618c0bf535a34f7dc6a28d51fa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33533687"
---
# <a name="how-to-layer-objects-on-windows-forms"></a>方法 : Windows フォーム上のオブジェクトをレイヤー化する
複雑なユーザー インターフェイスを作成またはマルチ ドキュメント インターフェイス (MDI) フォームを操作するときに多くの場合のコントロールと複雑なユーザー インターフェイス (UI) を作成する子フォームをレイヤーにします。 移動し、コントロールと windows グループのコンテキスト内での追跡を z オーダーを操作できます。 *Z オーダー* (深度) のフォームの z 軸に沿ってフォーム上のコントロールのビジュアルの重ね順がします。 Z オーダーの上部にあるウィンドウには、他のすべてのウィンドウが重複しています。 その他のすべての windows では、z オーダーの下部にあるウィンドウと重複します。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### <a name="to-layer-controls-at-design-time"></a>デザイン時にコントロールをレイヤーに  
  
1.  レイヤーにするコントロールを選択します。  
  
2.  **形式** メニューのをポイント**順序**、クリックして**前面へ移動**または**最背面へ移動**です。  
  
### <a name="to-layer-controls-programmatically"></a>コントロールをプログラムでレイヤーを  
  
-   使用して、<xref:System.Windows.Forms.Control.BringToFront%2A>と<xref:System.Windows.Forms.Control.SendToBack%2A>コントロールの z オーダーを操作するメソッド。  
  
     たとえば場合、<xref:System.Windows.Forms.TextBox>コントロール、`txtFirstName`はすぐ下に別制御したい場合一番上にある、次のコードを使用します。  
  
    ```vb  
    txtFirstName.BringToFront()  
    ```  
  
    ```csharp  
    txtFirstName.BringToFront();  
    ```  
  
    ```cpp  
    txtFirstName->BringToFront();  
    ```  
  
> [!NOTE]
>  Windows フォームをサポートしている*コントロール コンテインメント*です。 コントロール コンテインメントの数などのコンテナー コントロール内のコントロールの数に配置する<xref:System.Windows.Forms.RadioButton>内で制御、<xref:System.Windows.Forms.GroupBox>コントロール。 コントロールを格納しているコントロール内で、階層化することができます。 グループ化するボックスを移動すると、その内部に格納されているためにも、コントロールが移動します。  
  
## <a name="see-also"></a>関連項目  
 [Windows フォーム コントロール](../../../../docs/framework/winforms/controls/index.md)  
 [Windows フォームでのコントロールの配置](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [各 Windows フォーム コントロールのラベル設定とショートカットの作成](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [Windows フォームで使用するコントロール](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [Windows フォーム コントロールの機能別一覧](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
