---
title: "チュートリアル : Visual Basic での COM オブジェクトの作成"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- COM interop [Visual Basic], creating COM objects
- COM objects, creating
- COM interop [Visual Basic], walkthroughs
- object creation [Visual Basic], COM objects
- COM objects, walkthroughs
ms.assetid: 7b07a463-bc72-4392-9ba0-9dfcb697a44f
caps.latest.revision: "30"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ff7d3868a2e3ddaba06ebc6f98c8eacfc7299366
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-creating-com-objects-with-visual-basic"></a>チュートリアル : Visual Basic での COM オブジェクトの作成
新しいアプリケーションまたはコンポーネントを作成する場合は、.NET Framework アセンブリを作成することをお勧めします。 ただし、[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]も簡単に COM に .NET Framework コンポーネントの公開 これにより、COM コンポーネントを必要とする以前のアプリケーション スイートの新しいコンポーネントを提供することができます。 このチュートリアルを使用する方法を示します[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]を公開する[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]オブジェクトと COM クラス テンプレートを使用せず、COM オブジェクトとして。  
  
 COM オブジェクトを公開する最も簡単な方法は、COM クラス テンプレートを使用してです。 COM クラス テンプレートは、新しいクラスを作成し、構成、プロジェクトの COM オブジェクトとしてのクラスと相互運用性レイヤーを生成し、オペレーティング システムに登録します。  
  
> [!NOTE]
>  作成されたクラスを公開することもできます。 ただし[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]を使用するアンマネージ コードの COM オブジェクト、その場合は true。 COM オブジェクトではありませんとでは使用できません[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]です。 詳細については、次を参照してください。 [.NET Framework アプリケーションにおける COM 相互運用性](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)です。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-com-object-by-using-the-com-class-template"></a>COM クラス テンプレートを使用して COM オブジェクトを作成するには  
  
1.  新しい Windows アプリケーション プロジェクトを開き、**ファイル** をクリックしてメニュー**新しいプロジェクト**です。  
  
2.  **新しいプロジェクト**ダイアログ ボックスの 、**プロジェクトの種類**フィールドに、Windows が選択されていることを確認します。 選択**クラス ライブラリ**から、**テンプレート**一覧をクリックして**OK**です。 新しいプロジェクトが表示されます。  
  
3.  選択**新しい項目の追加**から、**プロジェクト**メニュー。 **[新しい項目の追加]** ダイアログ ボックスが表示されます。  
  
4.  選択**COM クラス**から、**テンプレート**一覧をクリックして**追加**です。 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]新しいクラスを追加し、COM 相互運用機能の新しいプロジェクトを構成します。  
  
5.  COM クラスには、プロパティ、メソッド、およびイベントのようなコードを追加します。  
  
6.  選択**ビルド ClassLibrary1**から、**ビルド**メニュー。 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]アセンブリがビルドされ、オペレーティング システムと COM オブジェクトを登録します。  
  
## <a name="creating-com-objects-without-the-com-class-template"></a>COM クラス テンプレートを使用せず、COM オブジェクトの作成  
 COM クラス テンプレートを使用する代わりに、手動での COM クラスを作成することもできます。 コマンドラインから作業している場合、または COM オブジェクトの定義方法を制御する場合は、この手順をお勧めします。  
  
#### <a name="to-set-up-your-project-to-generate-a-com-object"></a>COM オブジェクトを生成するプロジェクトを設定するには  
  
1.  新しい Windows アプリケーション プロジェクトを開き、**ファイル** をクリックしてメニュー**プロジェクトに新しい**です。  
  
2.  **新しいプロジェクト**ダイアログ ボックスの 、**プロジェクトの種類**フィールドに、Windows が選択されていることを確認します。 選択**クラス ライブラリ**から、**テンプレート**一覧をクリックして**OK**です。 新しいプロジェクトが表示されます。  
  
3.  **ソリューション エクスプ ローラー**、プロジェクトを右クリックし、クリックして**プロパティ**です。 **プロジェクト デザイナー**が表示されます。  
  
4.  **[コンパイル]** タブをクリックします。  
  
5.  選択、 **COM 相互運用機能の登録**チェック ボックスをオンします。  
  
#### <a name="to-set-up-the-code-in-your-class-to-create-a-com-object"></a>COM オブジェクトを作成する、クラスのコードを設定するには  
  
1.  **ソリューション エクスプ ローラー**をダブルクリックして**Class1.vb**そのコードを表示します。  
  
2.  クラスの名前を `ComClass1` に変更します。  
  
3.  次の定数を追加`ComClass1`です。 COM オブジェクトを必要とされる定数をグローバル一意識別子 (GUID) が格納されます。  
  
     [!code-vb[VbVbalrInterop#2](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_1.vb)]  
  
4.  **[ツール]** メニューの **[GUID の作成]**をクリックします。 **[GUID の作成]**ダイアログ ボックスで、**[レジストリ形式]** をクリックし、**[コピー]** をクリックします。 **[終了]** をクリックします。  
  
5.  空の文字列を置き換える、 `ClassId` GUID を持つ削除、先頭と末尾の右中かっこです。 たとえば、GUID が Guidgen によって提供される場合は`"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"`コードは次のように表示する必要があります。  
  
     [!code-vb[VbVbalrInterop#3](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_2.vb)]  
  
6.  前の手順を繰り返します、`InterfaceId`と`EventsId`定数は、次の例のようにします。  
  
     [!code-vb[VbVbalrInterop#4](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_3.vb)]  
  
    > [!NOTE]
    >  Guid は、新規および一意であることを確認してください。それ以外の場合、COM コンポーネントは、他の COM コンポーネントと競合する可能性があります。  
  
7.  追加、`ComClass`属性を`ComClass1`、次の例のように、クラス ID、インターフェイス ID、およびイベント ID の Guid を指定します。  
  
     [!code-vb[VbVbalrInterop#5](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_4.vb)]  
  
8.  COM クラスは、パラメーターなしである必要があります`Public Sub New()`コンス トラクター、またはクラスが正しく登録できません。 クラスには、パラメーターなしのコンス トラクターを追加します。  
  
     [!code-vb[VbVbalrInterop#6](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_5.vb)]  
  
9. 終了して、クラスのプロパティ、メソッド、およびイベントに追加、`End Class`ステートメントです。 選択**ソリューションのビルド**から、**ビルド**メニュー。 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]アセンブリがビルドされ、オペレーティング システムと COM オブジェクトを登録します。  
  
    > [!NOTE]
    >  使用して作成する COM オブジェクト[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]他のでは使用できません[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]アプリケーションは true。 COM オブジェクトではないためです。 このような COM オブジェクトへの参照を追加する操作には、エラーが発生します。 詳細については、「 [.NET Framework アプリケーションにおける COM 相互運用性](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)です。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.ComClassAttribute>  
 [COM 相互運用](../../../visual-basic/programming-guide/com-interop/index.md)  
 [チュートリアル : COM オブジェクトによる継承の実装](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)  
 [#Region ディレクティブ](../../../visual-basic/language-reference/directives/region-directive.md)  
 [.NET Framework アプリケーションにおける COM 相互運用性](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)  
 [相互運用性のトラブルシューティング](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)
