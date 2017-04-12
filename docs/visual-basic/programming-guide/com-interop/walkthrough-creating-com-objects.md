---
title: "チュートリアル: Visual Basic での COM オブジェクトの作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- COM interop, creating COM objects
- COM objects, creating
- COM interop, walkthroughs
- object creation, COM objects
- COM objects, walkthroughs
ms.assetid: 7b07a463-bc72-4392-9ba0-9dfcb697a44f
caps.latest.revision: 30
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: cce28e2be5914880107334bf2c4dc4dc645b4793
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-creating-com-objects-with-visual-basic"></a>チュートリアル : Visual Basic での COM オブジェクトの作成
新しいアプリケーションまたはコンポーネントを作成する場合は、.NET Framework アセンブリを作成することをお勧めします。 ただし、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]も容易に COM に .NET Framework コンポーネントを公開するには これにより、COM コンポーネントを必要とする以前のアプリケーション スイートに新しいコンポーネントを提供することができます。 このチュートリアルを使用する方法について説明[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]を公開する[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]COM オブジェクト、COM クラス テンプレートの有無にかかわらず、としてオブジェクトです。  
  
 COM オブジェクトを公開する最も簡単な方法は、COM クラス テンプレートを使用してです。 COM クラス テンプレートは、新しいクラスを作成し、COM オブジェクトとしてのクラスと相互運用性レイヤーを生成し、オペレーティング システムに登録するようにプロジェクトを構成します。  
  
> [!NOTE]
>  作成されたクラスを公開することもできます。 ただし[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]を使用するアンマネージ コードの COM オブジェクトとして true COM オブジェクトではない、では使用できません[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]します。 詳細については、次を参照してください。 [.NET Framework アプリケーションにおける COM 相互運用性](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)します。  
  
[!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### <a name="to-create-a-com-object-by-using-the-com-class-template"></a>COM クラス テンプレートを使用して COM オブジェクトを作成するには  
  
1.  新しい Windows アプリケーション プロジェクトを開き、**ファイル**をクリックしてメニュー**新しいプロジェクト**します。  
  
2.  **新しいプロジェクト**ダイアログ ボックスで 、**プロジェクトの種類**フィールドに、Windows が選択されていることを確認します。 選択**クラス ライブラリ**から、**テンプレート**一覧をクリックして**OK**します。 新しいプロジェクトが表示されます。  
  
3.  選択**新しい項目の追加**から、**プロジェクト**メニュー。 **新しい項目の追加** ダイアログ ボックスが表示されます。  
  
4.  選択**COM クラス**から、**テンプレート**一覧をクリックして**追加**します。 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]新しいクラスを追加し、COM 相互運用機能の新しいプロジェクトを構成します。  
  
5.  COM クラスには、プロパティ、メソッド、およびイベントのようなコードを追加します。  
  
6.  選択**ビルド ClassLibrary1**から、**ビルド**メニュー。 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]アセンブリがビルドされ、オペレーティング システムに COM オブジェクトを登録します。  
  
## <a name="creating-com-objects-without-the-com-class-template"></a>COM クラス テンプレートを使用せずに COM オブジェクトを作成します。  
 COM クラス テンプレートを使用する代わりに、手動での COM クラスを作成することもできます。 コマンドラインから作業している場合、または COM オブジェクトの定義方法を制御する場合は、この手順をお勧めします。  
  
#### <a name="to-set-up-your-project-to-generate-a-com-object"></a>COM オブジェクトを生成するプロジェクトを設定するには  
  
1.  新しい Windows アプリケーション プロジェクトを開き、**ファイル**をクリックしてメニュー **NewProject**します。  
  
2.  **新しいプロジェクト**ダイアログ ボックスで 、**プロジェクトの種類**フィールドに、Windows が選択されていることを確認します。 選択**クラス ライブラリ**から、**テンプレート**一覧をクリックして**OK**します。 新しいプロジェクトが表示されます。  
  
3.  **ソリューション エクスプ ローラー**、プロジェクトを右クリックし、クリックして**プロパティ**します。 **プロジェクト デザイナー**が表示されます。  
  
4.  **[コンパイル]** タブをクリックします。  
  
5.  選択、 **COM 相互運用機能の登録**チェック ボックスをオンします。  
  
#### <a name="to-set-up-the-code-in-your-class-to-create-a-com-object"></a>COM オブジェクトを作成する、クラスのコードを設定するには  
  
1.  **ソリューション エクスプ ローラー**をダブルクリックして**Class1.vb**そのコードを表示します。  
  
2.  クラスの名前を `ComClass1` に変更します。  
  
3.  次の定数を追加`ComClass1`します。 COM オブジェクトを持つ必要はグローバル一意識別子 (GUID) の定数が格納されます。  
  
     [!code-vb[VbVbalrInterop&#2;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_1.vb)]  
  
4.  **ツール** メニューのをクリックして**Guid の作成**します。 **GUID の作成**ダイアログ ボックスで、をクリックして**レジストリ形式** をクリックし、**コピー**します。 [ **終了**] をクリックします。  
  
5.  空の文字列を置き換える、 `ClassId` 、guid を削除、先頭と末尾の右中かっこです。 たとえば、Guidgen で GUID が提供される場合は`"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"`コードは次のように表示する必要があります。  
  
     [!code-vb[VbVbalrInterop&#3;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_2.vb)]  
  
6.  前の手順を繰り返します、`InterfaceId`と`EventsId`定数は、次の例に示すようにします。  
  
     [!code-vb[VbVbalrInterop&4;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_3.vb)]  
  
    > [!NOTE]
    >  Guid は、新規および一意であるかどうかを確認します。それ以外の場合、COM コンポーネントは、他の COM コンポーネントと競合する可能性があります。  
  
7.  追加、`ComClass`属性を`ComClass1`、クラス ID、インターフェイス ID、およびイベント ID の Guid を指定する例を次に示します。  
  
     [!code-vb[VbVbalrInterop&#5;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_4.vb)]  
  
8.  COM クラスが必要で、パラメーターなし`Public Sub New()`コンス トラクター、またはクラスが正しく登録されません。 クラスには、パラメーターなしのコンス トラクターを追加します。  
  
     [!code-vb[VbVbalrInterop&6;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_5.vb)]  
  
9. プロパティ、メソッド、およびイベントを終了して、クラスに追加、`End Class`ステートメントです。 選択**ソリューションのビルド**から、**ビルド**メニュー。 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]アセンブリがビルドされ、オペレーティング システムに COM オブジェクトを登録します。  
  
    > [!NOTE]
    >  COM オブジェクトを使用して作成する[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]他では使用できません[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]アプリケーションは true。 COM オブジェクトではないためです。 このような COM オブジェクトへの参照の追加を試行によってエラーが発生します。 詳細については、「 [.NET Framework アプリケーションにおける COM 相互運用性](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)します。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.ComClassAttribute></xref:Microsoft.VisualBasic.ComClassAttribute>   
 [COM 相互運用機能](../../../visual-basic/programming-guide/com-interop/index.md)   
 [チュートリアル: COM オブジェクトによる継承の実装](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)   
 [#Region ディレクティブ](../../../visual-basic/language-reference/directives/region-directive.md)   
 [.NET Framework アプリケーションにおける COM 相互運用性](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)   
 [相互運用性のトラブルシューティング](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)
