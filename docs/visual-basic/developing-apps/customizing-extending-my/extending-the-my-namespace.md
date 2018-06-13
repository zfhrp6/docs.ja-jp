---
title: Visual Basic における My 名前空間の拡張
ms.date: 07/20/2015
f1_keywords:
- vb.AddingMyExtensions
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
- My namespace [Visual Basic], extending
ms.assetid: 808e8617-b01c-4135-8b21-babe87389e8e
ms.openlocfilehash: 22d9d0def302b870de6f3e5ca4c142758b21314c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33591834"
---
# <a name="extending-the-my-namespace-in-visual-basic"></a>Visual Basic における My 名前空間の拡張
`My` Visual Basic での名前空間を簡単に活用するために、.NET Framework の機能を有効にするプロパティとメソッドを公開します。 `My`名前空間には多くの場合、1 行のコードに困難な作業を減らす、プログラミングの共通の問題が簡略化します。 さらに、`My`の動作をカスタマイズすることができるように、名前空間は完全に拡張可能`My`特定のアプリケーションのニーズに合わせて調整するには、その階層に新しいサービスを追加します。 このトピックでは両方の既存のメンバーをカスタマイズする方法、`My`名前空間に独自のカスタム クラスを追加する方法と、`My`名前空間。  
  
 **トピックの内容**  
  
-   [既存の My Namespace メンバーのカスタマイズ](#customizing)  
  
-   [My オブジェクトにメンバーを追加します。](#addingtoobjects)  
  
-   [カスタム オブジェクトを追加、My Namespace](#addingcustom)  
  
-   [メンバーを追加する、My Namespace](#addingtonamespace)  
  
-   [カスタム My オブジェクトへのイベントの追加](#addingevents)  
  
-   [デザイン ガイドライン](#design)  
  
-   [設計のクラス ライブラリの ](#designing)  
  
-   [パッケージ化と配置の拡張機能](#packaging)  
  
##  <a name="customizing"></a> 既存の My Namespace メンバーのカスタマイズ  
 `My` Visual Basic の公開で名前空間は、アプリケーション、自分のコンピューターに関する情報を頻繁に使用します。 内のオブジェクトの完全な一覧については、`My`名前空間を参照してください[マイ参照](../../../visual-basic/language-reference/keywords/my-reference.md)です。 既存のメンバーをカスタマイズする必要があります、`My`名前空間にするようは、アプリケーションのニーズを満たします。 内のオブジェクトの任意のプロパティ、`My`読み取り専用ではない名前空間は、カスタムの値に設定することができます。  
  
 たとえば、頻繁に使用する、`My.User`アプリケーションを実行しているユーザーの現在のセキュリティ コンテキストにアクセスするオブジェクト。 ただし、会社は、追加情報や企業内のユーザーの機能を公開するのにカスタムのユーザー オブジェクトを使用します。 このシナリオでの既定値を置き換えることができます、`My.User.CurrentPrincipal`次の例で示すように、独自カスタム プリンシパルのオブジェクトのインスタンスを持つプロパティです。  
  
 [!code-vb[VbVbcnExtendingMy#1](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/VisualBasic/extending-the-my-namespace_1.vb)]  
  
 設定、`CurrentPrincipal`プロパティを`My.User`オブジェクトが、アプリケーションを実行する id を変更します。 `My.User`オブジェクトは、さらに、新しく指定したユーザーに関する情報を返します。  
  
##  <a name="addingtoobjects"></a> My オブジェクトにメンバーを追加します。  
 返される型`My.Application`と`My.Computer`として定義されます`Partial`クラスです。 そのため、拡張することができます、`My.Application`と`My.Computer`オブジェクトを作成して、`Partial`という名前のクラス`MyApplication`または`MyComputer`です。 クラスにすることはできません、`Private`クラスです。 一部として、クラスを指定する場合、`My`名前空間、プロパティとに含まれているメソッドを追加できる、`My.Application`または`My.Computer`オブジェクト。  
  
 たとえば、次の例がという名前のプロパティを追加`DnsServerIPAddresses`を`My.Computer`オブジェクト。  
  
 [!code-vb[VbVbcnExtendingMy#2](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/VisualBasic/extending-the-my-namespace_2.vb)]  
  
##  <a name="addingcustom"></a> カスタム オブジェクトを追加、My Namespace  
 `My`名前空間は、多くの一般的なプログラミング タスクのソリューションを提供、作業が発生する可能性がある、`My`名前空間では対処できません。 たとえば、アプリケーションが、ユーザー データのカスタム ディレクトリ サービスにアクセスしたり、アプリケーションが Visual Basic での既定でインストールされていないアセンブリを使用可能性があります。 拡張することができます、`My`環境に固有の一般的なタスクへのカスタム ソリューションを含める名前空間。 `My`名前空間は、アプリケーションのニーズの増大に応じて新しいメンバーを追加に簡単に拡張できます。 さらに、展開することができます、`My`名前空間の拡張機能を Visual Basic テンプレートとして他の開発者。  
  
###  <a name="addingtonamespace"></a> メンバーを追加する、My Namespace  
 `My`名前空間には、その他の名前空間のようなことができますを追加する最上位のプロパティだけを追加して、モジュールを指定する、`Namespace`の`My`します。 モジュールに注釈を付ける、`HideModuleName`属性の次の例で示すようにします。 `HideModuleName`属性により、エントリのメンバーを表示するとき、IntelliSense は、モジュール名が表示されない、`My`名前空間。  
  
 [!code-vb[VbVbcnExtendingMy#3](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/VisualBasic/extending-the-my-namespace_3.vb)]  
  
 メンバーを追加する、`My`名前空間、モジュールに必要なプロパティを追加します。 追加の各プロパティについて、`My`名前空間、型のプライベート フィールドを追加`ThreadSafeObjectProvider(Of T)`型は、カスタム プロパティによって返される型です。 このフィールドは呼び出すことによって、プロパティによって返されるスレッド セーフであるオブジェクトのインスタンスの作成に使用、`GetInstance`メソッドです。 その結果、拡張プロパティにアクセスする各スレッドは、返される型のインスタンスを受け取ります。 次の例は、という名前のプロパティを追加`SampleExtension`型である`SampleExtension`を`My`名前空間。  
  
 [!code-vb[VbVbcnExtendingMy#4](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/VisualBasic/extending-the-my-namespace_4.vb)]  
  
##  <a name="addingevents"></a> カスタム My オブジェクトへのイベントの追加  
 使用することができます、`My.Application`独自のイベントを公開するオブジェクト`My`オブジェクトを拡張することによって、`MyApplication`部分クラスで、`My`名前空間。 ダブルクリックし、Windows ベースのプロジェクト、 **My Project**内のノードに、プロジェクトの**ソリューション エクスプ ローラー**です。 Visual Basic で**プロジェクト デザイナー**をクリックして、 `Application`  タブでをクリックし、`View Application Events`ボタンをクリックします。 ApplicationEvents.vb という新しいファイルが作成されます。 拡張するための次のコードが含まれている、`MyApplication`クラスです。  
  
 [!code-vb[VbVbcnExtendingMy#5](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/VisualBasic/extending-the-my-namespace_5.vb)]  
  
 イベント ハンドラーを追加するには独自の`My`オブジェクトへのカスタム イベント ハンドラーを追加することによって、`MyApplication`クラスです。 カスタム イベントを使用すると、イベント ハンドラーを追加すると、削除、またはイベントが発生したときに実行されるコードを追加できます。 なお、`AddHandler`コード、ユーザー イベントを処理するコードを追加した場合にのみ、カスタム イベントが実行されるためです。 たとえばを`SampleExtension`、前のセクションのオブジェクトが、`Load`のカスタム イベント ハンドラーを追加するイベントです。 次のコード例は、という名前のカスタム イベント ハンドラーを示しています。`SampleExtensionLoad`されるときに呼び出されます、`My.SampleExtension.Load`イベントが発生します。 新しいを処理するコードを追加するときに`My.SampleExtensionLoad`イベント、`AddHandler`このカスタム イベント コードの一部を実行します。 `MyApplication_SampleExtensionLoad`を処理するイベント ハンドラーの例を表示するコード例ではメソッドが含まれている、`My.SampleExtensionLoad`イベント。 なお、`SampleExtensionLoad`を選択すると、イベントが表示されます、**マイ アプリケーション イベント**左のドロップダウン リストの上、コード エディター、ApplicationEvents.vb ファイルを編集するときのオプションです。  
  
 [!code-vb[VbVbcnExtendingMy#6](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/VisualBasic/extending-the-my-namespace_6.vb)]  
  
##  <a name="design"></a> デザイン ガイドライン  
 拡張機能を開発する際に、`My`名前空間を拡張コンポーネントのメンテナンス コストを抑えるために、次のガイドラインを使用します。  
  
-   **拡張機能のロジックのみが含まれます。** 含まれるロジック、`My`名前空間の拡張機能に必要な機能を公開するために必要なコードのみを含める必要があります、`My`名前空間。 拡張機能は、ソース コードとしてユーザーのプロジェクトに存在するため拡張コンポーネントを更新高のメンテナンス コストが生じます、可能な限り避ける必要があります。  
  
-   **プロジェクトの前提条件を最小限に抑えます。** 拡張機能を作成する場合、`My`名前空間、参照、プロジェクト レベル インポート、または特定のコンパイラ設定のセットと仮定しないで (たとえば、`Option Strict`オフ)。 代わりに、依存関係を最小限にしを使用してすべての型参照を完全に修飾、`Global`キーワード。 また、拡張機能を使用してコンパイルすることを確認`Option Strict`の拡張機能でエラーを最小限にします。  
  
-   **拡張機能のコードを分離します。** Visual Studio 項目テンプレートと簡単に配置できる拡張機能は、1 つのファイルでコードを記述します。 詳細については、このトピックの「「のパッケージ化し、拡張機能の配置」を参照してください。 すべてを配置する、`My`名前空間の拡張機能コードを 1 つのファイルまたは別のフォルダーをプロジェクトにも役立ちますを検索するユーザー、`My`名前空間の拡張機能です。  
  
##  <a name="designing"></a> 設計のクラス ライブラリの   
 ほとんどのオブジェクト モデルと同様に、一部のデザイン パターンが適切に機能、`My`名前空間とその他のユーザーはこれはできません。 拡張機能を設計するとき、`My`名前空間には、次の原則を検討してください。  
  
-   **ステートレスな方法があります。** 内のメソッド、`My`名前空間は、特定のタスクへの完全なソリューションを提供する必要があります。 メソッドに渡されるパラメーター値が特定のタスクを完了するために必要なすべての入力を提供することを確認します。 リソースへの開いている接続など、前の状態に依存するメソッドを作成しないでください。  
  
-   **グローバル インスタンス。** 管理されている唯一の状態、`My`名前空間は、プロジェクトに対してグローバルです。 たとえば、`My.Application.Info`アプリケーション全体で共有されている状態をカプセル化します。  
  
-   **単純なパラメーターの型。** 複雑にならない複雑なパラメーターの型を回避することで。 代わりに、いずれかの入力パラメーターをとらないメソッドを作成するかを単純な入力文字列となど型、プリミティブ型にします。  
  
-   **ファクトリ メソッド。** 一部の型がインスタンス化するが困難とは限りません。 ファクトリ メソッドを提供する拡張機能として、`My`名前空間より簡単に検出し、このカテゴリに分類される型を使用することができます。 適切に動作するためのファクトリ メソッドの例は`My.Computer.FileSystem.OpenTextFileReader`します。 いくつかのストリーム型は .NET Framework で使用できます。 具体的には、テキスト ファイルを指定することによって、`OpenTextFileReader`ユーザーが使用するストリームを理解するのに役立ちます。  
  
 次のガイドラインは、クラス ライブラリに関する一般的な設計の原則を妨害しません。 代わりに、Visual Basic を使用する開発者用に最適化された推奨事項は、`My`名前空間。 クラス ライブラリを作成するための一般的な設計原則を参照してください。 [Framework デザイン ガイドライン](../../../standard/design-guidelines/index.md)です。  
  
##  <a name="packaging"></a> パッケージ化と配置の拡張機能  
 含めることができます`My`には、Visual Studio プロジェクト テンプレートでは、名前空間の拡張機能が、拡張機能をパッケージ化し、し、Visual Studio 項目テンプレートとして展開できます。 パッケージ化するときに、 `My` Visual Studio 項目テンプレートと名前空間拡張を行う Visual Basic で提供される追加機能を活用します。 これらの機能を使用するプロジェクトは、特定のアセンブリを参照するときに、拡張機能を含めるまたは明示的に追加するユーザーを有効にする、`My`名前空間の拡張機能を使用して、**マイ拡張**Visual Basic のページプロジェクト デザイナー。  
  
 展開する方法の詳細について`My`名前空間の拡張機能を参照してください[パッケージ化とカスタム My 拡張機能の配置](../../../visual-basic/developing-apps/customizing-extending-my/packaging-and-deploying-custom-my-extensions.md)です。  
  
## <a name="see-also"></a>関連項目  
 [カスタム My 拡張のパッケージ化と配置](../../../visual-basic/developing-apps/customizing-extending-my/packaging-and-deploying-custom-my-extensions.md)  
 [Visual Basic アプリケーション モデルの拡張](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)  
 [My で利用可能なオブジェクトのカスタマイズ](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)  
 [[マイ拡張] ページ、プロジェクト デザイナー](/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)  
 [[アプリケーション] ページ (プロジェクト デザイナー)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)  
 [Partial](../../../visual-basic/language-reference/modifiers/partial.md)
