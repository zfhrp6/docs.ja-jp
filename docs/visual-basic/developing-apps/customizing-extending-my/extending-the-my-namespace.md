---
title: "拡張する、Visual Basic では、My Namespace |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.AddingMyExtensions
dev_langs:
- VB
helpviewer_keywords:
- My namespace, customizing
- My namespace
- My namespace, extending
ms.assetid: 808e8617-b01c-4135-8b21-babe87389e8e
caps.latest.revision: 13
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: 1d1e957536f35b81a9672994c9d4d261afb764ea
ms.lasthandoff: 03/13/2017

---
# <a name="extending-the-my-namespace-in-visual-basic"></a>Visual Basic における My 名前空間の拡張
`My` Visual Basic における名前空間は、プロパティおよび .NET Framework の能力を簡単に利用するためのメソッドを公開します。 `My`名前空間には、一般的なプログラミング上の問題、多くの場合、1 行のコードに困難な作業を減らすことが簡略化されます。 さらに、`My`の動作をカスタマイズできるように、名前空間は完全に拡張可能`My`し、その階層の特定のアプリケーションのニーズに対応する新しいサービスを追加します。 このトピックでは両方の既存のメンバーをカスタマイズする方法、`My`名前空間に、独自のカスタム クラスを追加する方法と、`My`名前空間。  
  
 **トピック目次**  
  
-   [既存の My Namespace メンバーのカスタマイズ](#customizing)  
  
-   [My オブジェクトにメンバーを追加します。](#addingtoobjects)  
  
-   [カスタム オブジェクトを追加、My Namespace](#addingcustom)  
  
-   [メンバーを追加する、My Namespace](#addingtonamespace)  
  
-   [カスタム My オブジェクトへのイベントの追加](#addingevents)  
  
-   [デザインのガイドライン](#design)  
  
-   [用のクラス ライブラリをデザイン、](#designing)  
  
-   [パッケージ化と配置の拡張機能](#packaging)  
  
##  <a name="customizing"></a>既存の My Namespace メンバーのカスタマイズ  
 `My`公開の Visual Basic で名前空間は、アプリケーションや、コンピューターに関する情報を頻繁に使用します。 内のオブジェクトの完全な一覧については、`My`名前空間を参照してください[マイ参照](../../../visual-basic/language-reference/keywords/my-reference.md)します。 既存のメンバーをカスタマイズする必要があります、`My`名前空間するよう、アプリケーションのニーズに合致しています。 内のオブジェクトのプロパティ、`My`が読み取り専用でない名前空間は、カスタムの値に設定することができます。  
  
 たとえば、頻繁に使用すると仮定、`My.User`アプリケーションを実行しているユーザーの現在のセキュリティ コンテキストにアクセスするオブジェクト。 ただし、会社では、カスタムのユーザー オブジェクトを使用して、追加情報と、企業内のユーザー用の機能を公開します。 このシナリオでの既定値を置き換えることができます、`My.User.CurrentPrincipal`次の例で示すように、独自カスタム プリンシパルのオブジェクトのインスタンスを持つプロパティです。  
  
 [!code-vb[VbVbcnExtendingMy&#1;](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/VisualBasic/extending-the-my-namespace_1.vb)]  
  
 設定、`CurrentPrincipal`プロパティを`My.User`オブジェクトが、アプリケーションを実行する id を変更します。 `My.User`オブジェクトは、さらに、新しく指定したユーザーに関する情報を返します。  
  
##  <a name="addingtoobjects"></a>My オブジェクトにメンバーを追加します。  
 返される型`My.Application`と`My.Computer`として定義された`Partial`クラスです。 そのため、拡張することができます、`My.Application`と`My.Computer`オブジェクトを作成することで、`Partial`という名前のクラス`MyApplication`または`MyComputer`です。 クラスにすることはできません、`Private`クラスです。 一部として、クラスを指定する場合、`My`名前空間、プロパティとは含まれているメソッドを追加できる、`My.Application`または`My.Computer`オブジェクトです。  
  
 たとえば、次の例がという名前のプロパティを追加`DnsServerIPAddresses`に、`My.Computer`オブジェクトです。  
  
 [!code-vb[VbVbcnExtendingMy&#2;](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/VisualBasic/extending-the-my-namespace_2.vb)]  
  
##  <a name="addingcustom"></a>カスタム オブジェクトを追加、My Namespace  
 ですが、`My`名前空間は、多くの一般的なプログラミング タスクの解決方法、タスクが表示される可能性を`My`名前空間では取り上げません。 たとえば、アプリケーションが、ユーザー データのカスタム ディレクトリ サービスにアクセスまたは Visual Basic では、既定でインストールされていないアセンブリ、アプリケーションを使用しています。 拡張する、`My`名前空間は、環境に固有の一般的なタスクへのカスタム ソリューションを含めます。 `My`名前空間は、増え続けるアプリケーションのニーズを満たす新しいメンバーを追加する簡単に拡張できます。 さらに、展開、`My`名前空間の拡張を Visual Basic テンプレートとして他の開発者です。  
  
###  <a name="addingtonamespace"></a>メンバーを追加する、My Namespace  
 `My`名前空間には、他の名前空間のようにプロパティを追加できます最上位レベルにモジュールを追加して、指定するだけで、`Namespace`の`My`です。 使用して、モジュールに注釈を付ける、`HideModuleName`属性の次の例で示すようにします。 `HideModuleName`属性により、IntelliSense は表示されないように、モジュール名のメンバーを表示するとき、`My`名前空間。  
  
 [!code-vb[VbVbcnExtendingMy&#3;](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/VisualBasic/extending-the-my-namespace_3.vb)]  
  
 メンバーを追加する、`My`名前空間、モジュールに必要に応じてプロパティを追加します。 追加されたプロパティごとに、`My`名前空間、型のプライベート フィールドを追加`ThreadSafeObjectProvider(Of T)`型は、カスタム プロパティによって返される型。 このフィールドは呼び出すことによって、プロパティによって返されるスレッド セーフなオブジェクト インスタンスの作成に使用、`GetInstance`メソッドです。 その結果、拡張プロパティにアクセスしている各スレッドは、返される型のインスタンスを受け取ります。 次の例は、という名前のプロパティを追加`SampleExtension`型のある`SampleExtension`に、`My`名前空間。  
  
 [!code-vb[VbVbcnExtendingMy&4;](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/VisualBasic/extending-the-my-namespace_4.vb)]  
  
##  <a name="addingevents"></a>カスタム My オブジェクトへのイベントの追加  
 使用することができます、`My.Application`独自のイベントを公開するオブジェクト`My`オブジェクトを拡張することによって、`MyApplication`部分クラスに、`My`名前空間。 ダブルクリックし、Windows ベースのプロジェクト、 **My Project**内のノードに、プロジェクトの**ソリューション エクスプ ローラー**します。 Visual Basic で**プロジェクト デザイナー**、 をクリックして、 `Application`  タブでをクリックし、 `View Application Events`  ボタンをクリックします。 ApplicationEvents.vb という新しいファイルが作成されます。 拡張するための次のコードが含まれている、`MyApplication`クラスです。  
  
 [!code-vb[VbVbcnExtendingMy&#5;](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/VisualBasic/extending-the-my-namespace_5.vb)]  
  
 イベント ハンドラーを追加するには独自の`My`オブジェクトへのカスタム イベント ハンドラーを追加することで、`MyApplication`クラスです。 カスタム イベントを使用すると、イベント ハンドラーを追加すると、削除、またはイベントが発生したときに実行されるコードを追加できます。 なお、`AddHandler`コード カスタム イベントがイベントを処理するユーザー コードを追加した場合にのみを実行するためのです。 たとえば、それを考慮して、`SampleExtension`前のセクションからオブジェクトには、`Load`のカスタム イベント ハンドラーを追加するイベントです。 次のコード例は、という名前のカスタム イベント ハンドラーを示しています。`SampleExtensionLoad`されるするときに呼び出さ、`My.SampleExtension.Load`イベントが発生します。 新しいを処理するコードを追加するときに`My.SampleExtensionLoad`、イベント、`AddHandler`このカスタム イベント コードの一部を実行します。 `MyApplication_SampleExtensionLoad`を処理するイベント ハンドラーの例を示すコード例ではメソッドが含まれている、`My.SampleExtensionLoad`イベントです。 注意してください、`SampleExtensionLoad`を決めるときに、イベントが使用できる、**マイ アプリケーション イベント**左側のドロップダウン リスト、コード エディターの上、ApplicationEvents.vb ファイルを編集するときにオプション。  
  
 [!code-vb[VbVbcnExtendingMy&6;](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/VisualBasic/extending-the-my-namespace_6.vb)]  
  
##  <a name="design"></a>デザインのガイドライン  
 拡張機能を開発する場合、`My`名前空間、拡張コンポーネントのメンテナンス コストを最小限に抑えるために、次のガイドラインを使用します。  
  
-   **拡張機能のロジックのみが含まれます。** 含まれるロジック、`My`名前空間の拡張機能に必要な機能を公開するために必要なコードのみを含める必要があります、`My`名前空間。 拡張機能は、ソース コードとしてユーザー プロジェクトに存在するため拡張コンポーネントを更新、高のメンテナンス コストが発生し、可能な限り避ける必要があります。  
  
-   **プロジェクトの前提条件を最小化します。** 拡張機能を作成する場合、`My`名前空間、参照、プロジェクト レベルのインポート、または特定のコンパイラ設定のセットと仮定しないで (たとえば、`Option Strict`オフ) です。 代わりに、依存関係を最小限にしを使用してすべての型参照を完全に修飾、`Global`キーワードです。 またで、拡張機能がコンパイルされることを確認`Option Strict`の拡張機能のエラーを最小限にします。  
  
-   **拡張機能のコードを分離します。** Visual Studio 項目テンプレートとして簡単に展開できる、拡張機能は、1 つのファイルのコードを記述します。 詳細については、このトピックの後半の「パッケージ化および展開する拡張機能」を参照してください。 すべてを配置する、`My`名前空間の拡張機能コードを単一のファイルまたは別のフォルダー、プロジェクトにも役立つ検索、`My`名前空間の拡張機能です。  
  
##  <a name="designing"></a>用のクラス ライブラリをデザイン、  
 ほとんどのオブジェクト モデルの場合と同様に、一部のデザイン パターンが正常に動作、`My`名前空間とその他のユーザーはありません。 拡張機能を設計する際、`My`名前空間には、次の原則を検討してください。  
  
-   **ステートレスな方法があります。** 内のメソッド、`My`名前空間は、特定のタスクに完全なソリューションを提供する必要があります。 メソッドに渡されるパラメーター値が特定のタスクを完了するために必要なすべての入力を提供することを確認します。 リソースへの接続などの以前の状態に依存するメソッドを作成しないでください。  
  
-   **グローバルのインスタンス。** 管理されている唯一の状態、`My`名前空間は、プロジェクトに対してグローバルです。 たとえば、`My.Application.Info`アプリケーション全体で共有されている状態をカプセル化します。  
  
-   **単純なパラメーターの型。** 簡潔さの複雑なパラメーターの型を回避することで。 パラメーターの入力を受け取らないメソッドの代わりに、作成し、文字列、プリミティブ型などの簡単な入力型がかかります。  
  
-   **ファクトリ メソッド。** 一部の型がインスタンス化することが困難です。 ファクトリ メソッドを提供する拡張機能として、`My`名前空間を使用するより簡単に検出し、このカテゴリに分類される型を使用します。 適切に動作するためのファクトリ メソッドの例としては`My.Computer.FileSystem.OpenTextFileReader`です。 ストリーム型がいくつかは、.NET Framework で使用できます。 具体的には、テキスト ファイルを指定することによって、`OpenTextFileReader`を使用するストリームをユーザーに役立ちます。  
  
 次のガイドラインは、クラス ライブラリに関する一般的な設計原則を妨害しません。 Visual Basic を使用する開発者向けに最適化された推奨事項を正確には、`My`名前空間。 クラス ライブラリを作成するための一般的な設計原則を参照してください。 [Framework デザイン ガイドライン](http://msdn.microsoft.com/library/5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b)します。  
  
##  <a name="packaging"></a>パッケージ化と配置の拡張機能  
 含めることができます`My`には、Visual Studio プロジェクト テンプレートでは、名前空間の拡張は、拡張機能をパッケージ化し、Visual Studio 項目テンプレートとして配置します。 パッケージ化するときに、 `My` Visual Studio 項目テンプレートと名前空間の拡張、Visual Basic で提供される追加の機能の利点を行えます。 これらの機能を使用するプロジェクトは、特定のアセンブリを参照するときに、拡張機能を含めるまたは明示的に追加するユーザーを有効にする、`My`名前空間の拡張機能を使用して、 **My 拡張**Visual Basic プロジェクト デザイナーのページです。  
  
 展開する方法の詳細について`My`名前空間の拡張機能を参照してください[パッケージ化と展開のカスタム My 拡張](../../../visual-basic/developing-apps/customizing-extending-my/packaging-and-deploying-custom-my-extensions.md)します。  
  
## <a name="see-also"></a>関連項目  
 [カスタム マイ拡張のパッケージ化と配置](../../../visual-basic/developing-apps/customizing-extending-my/packaging-and-deploying-custom-my-extensions.md)   
 [Visual Basic アプリケーション モデルの拡張](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)   
 [利用可能なオブジェクトのカスタマイズ ](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)   
 [マイ拡張 ページ、プロジェクト デザイナー](https://docs.microsoft.com/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)   
 [[アプリケーション] ページ (プロジェクト デザイナー) (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/application-page-project-designer-visual-basic)   
 [Partial](../../../visual-basic/language-reference/modifiers/partial.md)
