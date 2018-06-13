---
title: コントロールの種類に関するアドバイス
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- user controls [Windows Forms], when to use
- custom controls [Windows Forms], types
- controls [Windows Forms], creating
ms.assetid: 5235fe9d-c36a-4c08-ae76-6cb90b50085e
ms.openlocfilehash: d6a2b663c566aae48c694ffc335fcef0ce24034f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33528945"
---
# <a name="control-type-recommendations"></a>コントロールの種類に関するアドバイス
.NET Framework は、新しいコントロールを開発して実装する機能を提供します。 使い慣れたユーザー コントロールだけでなく、独自の描画を実行するカスタム コントロールを作成することも、継承によって既存のコントロールの機能を拡張することもできるようになりました。 作成するコントロールの種類の決定が、混乱を招く可能性があります。 このセクションでは、継承できるさまざまな種類のコントロールの間の違いについて説明し、プロジェクトに合わせて選択する種類に関する注意点を示しています。  
  
> [!NOTE]
>  Web フォームで使用するコントロールを作成する場合は、「[カスタム ASP.NET サーバー コントロールの開発](http://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef)」を参照してください。  
  
## <a name="inheriting-from-a-windows-forms-control"></a>Windows フォーム コントロールからの継承  
 既存の Windows フォーム コントロールから継承されたコントロールを派生できます。 この方法では、すべての Windows フォーム コントロールの本質的な機能をすべて保持して、カスタム プロパティ、メソッド、またはその他の機能を追加することでその機能を拡張することができます。 たとえば、数値のみを受け付け、入力を自動的に値に変換できる <xref:System.Windows.Forms.TextBox> から派生したコントロールを作成することができます。 このようなコントロールには、テキスト ボックスのテキストが変更されるたびに呼び出される検証コードが含まれ、値のプロパティを追加で持つことができます。 一部のコントロールでは、基本クラスの <xref:System.Windows.Forms.Control.OnPaint%2A> メソッドをオーバーライドすることで、コントロールのグラフィカル インターフェイスにカスタムの外観を追加することができます。  
  
 次の場合に、Windows フォーム コントロールから継承します。  
  
-   必要とする機能のほとんどが、既存の Windows フォーム コントロールと同じです。  
  
-   カスタムのグラフィカル インターフェイスが必要ないか、または既存のコントロールに対して新しいグラフィカルのフロント エンドをデザインします。  
  
## <a name="inheriting-from-the-usercontrol-class"></a>UserControl クラスを継承する  
 ユーザー コントロールは、共通のコンテナー内にカプセル化された Windows フォーム コントロールのコレクションです。 コンテナーは、各 Windows フォーム コントロールに関連付けられている固有の機能をすべて保持し、それらのプロパティを選択的に公開してバインドすることができます。 ユーザー コントロールの例として、データベースから顧客の住所データを表示する貯めに作成されたコントロールがあります。 このコントロールには、各フィールドを表示するいくつかのテキスト ボックスと、レコード間を移動するボタン コントロールが含まれます。 データ バインドのプロパティは選択的に公開することができ、コントロール全体は、パッケージしてアプリケーション間で再利用できます。  
  
 次の場合に、<xref:System.Windows.Forms.UserControl> クラスから継承します。  
  
-   いくつかの Windows フォーム コントロールの機能を再利用可能な 1 つの単位に結合します。  
  
## <a name="inheriting-from-the-control-class"></a>Control クラスからの継承  
 コントロールを作成する別の方法は、<xref:System.Windows.Forms.Control> から継承することで、実質的に一から作成する方法です。 <xref:System.Windows.Forms.Control> クラスは、コントロール (イベントなど) によって必要とされる基本的な機能をすべて提供しますが、コントロール固有の機能やグラフィカル インターフェイスは提供しません。 <xref:System.Windows.Forms.Control> クラスから継承することでコントロールを作成する場合は、ユーザー コントロールや既存の Windows フォーム コントロールから継承する場合よりも、はるかに多くの配慮と労力が必要です。 作成者は、コントロールの <xref:System.Windows.Forms.Control.OnPaint%2A> イベントのコード、および必要とされる機能固有のコードを作成する必要があります。 ただし、より大きな柔軟性が可能になり、正確なニーズに合わせてコントロールをカスタムに調整することができます。 カスタム コントロールの例は、アナログ時計の外観や動作を複製する時計コントロールです。 内部タイマー コンポーネントからの <xref:System.Windows.Forms.Timer.Tick> イベントに応答してカスタム描画が呼び出されて、時計の針が移動します。  
  
 次の場合に、<xref:System.Windows.Forms.Control> クラスから継承します。  
  
-   コントロールのカスタムのグラフィカル表現を提供します。  
  
-   標準コントロールでは使用できないカスタムの機能を実装する必要があります。  
  
-   [方法: [ツールボックス アイテムの選択] ダイアログ ボックスにコントロールを表示する](http://msdn.microsoft.com/library/9yxtkx75\(v=vs.110\))  
  
-   [チュートリアル: DesignerSerializationVisibilityAttribute を使用した、標準データ型のコレクションのシリアル化](http://msdn.microsoft.com/library/ms171731\(v=vs.110\))  
  
-   [チュートリアル : Visual C# による Windows フォーム コントロールからの継承](http://msdn.microsoft.com/library/5h0k2e6x\(v=vs.110\))  
  
-   [方法 : コントロールにツールボックス ビットマップを指定する](http://msdn.microsoft.com/library/4wk1wc0a\(v=vs.110\))  
  
-   [方法: 既存の Windows フォーム コントロールから継承する](http://msdn.microsoft.com/library/7h62478z\(v=vs.110\))  
  
-   [チュートリアル: カスタム Windows フォーム コントロールのデザイン時のデバッグ](http://msdn.microsoft.com/library/5ytx0z24\(v=vs.110\))  
  
-   [方法: コントロール クラスを継承する](http://msdn.microsoft.com/library/skcysbt2\(v=vs.110\))  
  
-   [方法: UserControl の実行時の動作をテストする](http://msdn.microsoft.com/library/ms171738\(v=vs.110\))  
  
-   [方法: デザイン時にフォームの端に合わせてコントロールを配置する](http://msdn.microsoft.com/library/1fxyb15b\(v=vs.110\))  
  
-   [方法: UserControl クラスを継承する](http://msdn.microsoft.com/library/00ctb4z0\(v=vs.110\))  
  
-   [方法: Windows フォームのコントロールを作成する](http://msdn.microsoft.com/library/bs3yhkh7\(v=vs.110\))  
  
-   [方法: 複合コントロールを作成する](http://msdn.microsoft.com/library/3sf86w5h\(v=vs.110\))  
  
-   [チュートリアル : Visual Basic による複合コントロールの作成](http://msdn.microsoft.com/library/c316f119\(v=vs.110\))  
  
-   [チュートリアル: Visual C# による複合コントロールの作成](http://msdn.microsoft.com/library/a6h7e207\(v=vs.110\))  
  
-   [チュートリアル : Visual Basic による Windows フォーム コントロールからの継承](http://msdn.microsoft.com/library/w2a8y03d\(v=vs.110\))  
  
-   [方法: デザイン時機能を活用した Windows フォーム コントロールを作成する](http://msdn.microsoft.com/library/307hck25\(v=vs.110\))  
  
-   [方法: デザイン時機能を活用した Windows フォーム コントロールを作成する](http://msdn.microsoft.com/library/307hck25\(v=vs.120\))  
  
## <a name="see-also"></a>関連項目  
 [方法: シンプルな Windows フォーム コントロールを開発する](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md)  
 [さまざまなカスタム コントロール](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
