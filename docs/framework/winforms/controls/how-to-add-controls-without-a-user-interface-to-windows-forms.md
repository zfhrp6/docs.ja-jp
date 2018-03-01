---
title: "方法 : ユーザー インターフェイスを持たないコントロールを Windows フォームに追加する"
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
- cpp
f1_keywords:
- NonVisualSelection
helpviewer_keywords:
- invisible controls [Windows Forms]
- Windows Forms controls, adding to form
- controls [Windows Forms], nonvisual
- Windows Forms controls, nonvisual
- nonvisual controls [Windows Forms]
ms.assetid: 52134d9c-cff6-4eed-8e2b-3d5eb3bd494e
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3abbf931cff9ad459e8c9221f91430ecccefa9cc
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-add-controls-without-a-user-interface-to-windows-forms"></a>方法 : ユーザー インターフェイスを持たないコントロールを Windows フォームに追加する
非ビジュアル コントロール (またはコンポーネント) は、アプリケーションに機能を提供します。 異なり、他のコントロールのコンポーネント、ユーザーにユーザー インターフェイスを提供しないので、Windows フォーム デザイナー画面に表示する必要はありません。 コンポーネントがフォームに追加されると、Windows フォーム デザイナーは、すべてのコンポーネントが表示されるフォームの下部にあるサイズ変更可能なトレイを表示します。 コントロールがコンポーネント トレイに追加されると、コンポーネントを選択し、フォーム上の他のコントロールのように、そのプロパティを設定することができます。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### <a name="to-add-a-component-to-a-windows-form"></a>Windows フォームにコンポーネントを追加するには  
  
1.  フォームを開きます。 詳細については、「[する方法: デザイナーでの Windows フォームの表示](http://msdn.microsoft.com/library/bf3f1e5b-ea07-4529-85c6-6af3ded0cec5)です。  
  
2.  **ツールボックス**コンポーネントをクリックし、フォームにドラッグします。  
  
     コンポーネントがコンポーネント トレイに表示されます。  
  
 さらに、コンポーネントは、実行時にフォームに追加できます。 これは、コンポーネントにはユーザー インターフェイスを持つコントロールとは異なり、ビジュアルの式があるないために特に一般的なシナリオです。 次の例で、<xref:System.Windows.Forms.Timer>実行時にコンポーネントを追加します。 (なお[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]異なるタイマーの数が含まれています。 この場合、を使用して Windows フォーム<xref:System.Windows.Forms.Timer>コンポーネントです。 別のタイマーの詳細については[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]を参照してください[サーバー ベースのタイマーの概要](http://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc))。  
  
> [!CAUTION]
>  コンポーネントには、コンポーネントを効果的に機能するために設定する必要があるコントロール固有プロパティが多くの場合があります。 場合、<xref:System.Windows.Forms.Timer>下のコンポーネントを設定する、`Interval`プロパティです。 プロジェクトにあるプロパティを設定する、そのコンポーネントに必要なコンポーネントを追加するときにことを確認します。  
  
#### <a name="to-add-a-component-to-a-windows-form-programmatically"></a>Windows フォームにプログラムでコンポーネントを追加するには  
  
1.  インスタンスを作成、<xref:System.Windows.Forms.Timer>コード内のクラスです。  
  
2.  設定、`Interval`タイマーのティック間の時間を決定するプロパティです。  
  
3.  コンポーネントに必要なその他のプロパティを構成します。  
  
     次のコードの作成を示しています、<xref:System.Windows.Forms.Timer>でその`Interval`プロパティ セットです。  
  
    ```vb  
    Public Sub CreateTimer()  
       Dim timerKeepTrack As New System.Windows.Forms.Timer  
       timerKeepTrack.Interval = 1000  
    End Sub  
    ```  
  
    ```csharp  
    public void createTimer()  
    {  
       System.Windows.Forms.Timer timerKeepTrack = new  
           System.Windows.Forms.Timer();  
       timerKeepTrack.Interval = 1000;  
    }  
    ```  
  
    ```cpp  
    public:  
       void createTimer()  
       {  
          System::Windows::Forms::Timer^ timerKeepTrack = gcnew  
             System::Windows::Forms::Timer();  
          timerKeepTrack->Interval = 1000;  
       }  
    ```  
  
    > [!IMPORTANT]
    >  悪意のあるユーザー コントロールを参照することで、ローカル コンピューターがネットワーク経由のセキュリティ リスクを公開する可能性があります。 誤ってそれをプロジェクトに追加した後に、有害なカスタム コントロールを作成する悪意のあるユーザーの場合は問題にならなければのみとなります。  
  
## <a name="see-also"></a>参照  
 [Windows フォーム コントロール](../../../../docs/framework/winforms/controls/index.md)  
 [方法: Windows フォームにコントロールを追加する](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)  
 [方法: Windows フォームに ActiveX コントロールを追加する](../../../../docs/framework/winforms/controls/how-to-add-activex-controls-to-windows-forms.md)  
 [方法: Windows フォーム間でコントロールをコピーする](../../../../docs/framework/winforms/controls/how-to-copy-controls-between-windows-forms.md)  
 [Windows フォームへのコントロールの追加](../../../../docs/framework/winforms/controls/putting-controls-on-windows-forms.md)  
 [各 Windows フォーム コントロールのラベル設定とショートカットの作成](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [Windows フォームで使用するコントロール](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [Windows フォーム コントロールの機能別一覧](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
