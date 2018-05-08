---
title: '方法 : Windows フォームに単純バインド コントロールを作成する'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [Windows Forms], simple data binding
- Windows Forms controls, data binding
ms.assetid: 3bcaded8-0f1a-4cc0-8830-f59be253bf4e
ms.openlocfilehash: ce4585a1c5c2b9acbdb7ec33c62a1e91851b720e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-simple-bound-control-on-a-windows-form"></a>方法 : Windows フォームに単純バインド コントロールを作成する
*単純バインディング*、コントロールがデータセット テーブルの列の値など、1 つのデータ要素を表示することができます。 できる単純なをバインドするコントロールの任意のプロパティ データ値。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### <a name="to-simple-bind-a-control"></a>単純なコントロールをバインドする  
  
1.  データ ソースに接続します。 詳細については、次を参照してください。[データ ソースに接続する](../../../docs/framework/data/adonet/connecting-to-a-data-source.md)です。  
  
2.  フォームでコントロールを選択し、表示、**プロパティ**ウィンドウです。  
  
3.  展開して、 **(DataBindings)** プロパティです。  
  
     最も頻繁にバインドされているプロパティは、下に表示されます、 **(DataBindings)** プロパティです。 たとえば、ほとんどのコントロールで、**テキスト**プロパティが最も頻繁に連結します。  
  
4.  場合、プロパティにバインド一般的にバインドされたプロパティの 1 つはありません をクリックして、**省略記号**ボタン (![VisualStudioEllipsesButton スクリーン ショット](../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) で、 **(詳細)** を表示するボックス、**フォーマットと詳細バインド**そのコントロールのプロパティの完全な一覧がダイアログ ボックス。  
  
5.  下にあるドロップダウン矢印をクリックし、バインドするプロパティを選択する**バインド**です。  
  
     使用できるデータ ソースの一覧が表示されます。  
  
6.  目的の 1 つのデータ要素が見つかるまで、バインド先のデータ ソースを展開します。 たとえば、データセットのテーブル内の列の値にバインドする場合は、データセットの名前を展開し、次にテーブル名を展開して、列名を表示します。  
  
7.  バインド先の要素の名前をクリックします。  
  
8.  作業している場合、**フォーマットと詳細バインド**ダイアログ ボックスで、をクリックして**OK**に戻るには、**プロパティ**ウィンドウ。  
  
9. コントロールの追加のプロパティをバインドする場合は、手順 3. ~ 7. を繰り返します。  
  
    > [!NOTE]
    >  単純バインド コントロールでは、単一のデータ要素のみを表示するため、Windows フォームに単純バインド コントロールにナビゲーション ロジックを含めるごく一般的なものです。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.Binding>  
 [Windows フォームでのデータ バインディング](../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [データ連結と Windows フォーム](../../../docs/framework/winforms/data-binding-and-windows-forms.md)
