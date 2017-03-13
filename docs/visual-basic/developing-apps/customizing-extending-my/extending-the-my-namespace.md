---
title: "Extending the My Namespace in Visual Basic | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.AddingMyExtensions"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "My namespace, customizing"
  - "My namespace"
  - "My namespace, extending"
ms.assetid: 808e8617-b01c-4135-8b21-babe87389e8e
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 13
---
# Extending the My Namespace in Visual Basic
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

Visual Basic の `My` 名前空間は、.NET Framework の機能を簡単に活用できるようにするプロパティとメソッドを公開します。  `My` 名前空間を使用すると、プログラミング上の一般的な問題が簡単になり、多くの場合、難しい作業でも 1 行のコードにまとめることができます。  さらに `My` 名前空間は十分な拡張性があるため、`My` の動作をカスタマイズしてその階層に新しいサービスを追加することで、特定のアプリケーションのニーズに対応できます。  このトピックでは、`My` 名前空間の既存のメンバーをカスタマイズする方法と、独自のカスタム クラスを `My` 名前空間に追加する方法の両方について説明します。  
  
 **トピック目次**  
  
-   [既存の My 名前空間メンバーのカスタマイズ](#customizing)  
  
-   [My オブジェクトへのメンバーの追加](#addingtoobjects)  
  
-   [My 名前空間へのカスタム オブジェクトの追加](#addingcustom)  
  
-   [My 名前空間へのメンバーの追加](#addingtonamespace)  
  
-   [カスタム My オブジェクトへのイベントの追加](#addingevents)  
  
-   [デザイン ガイドライン](#design)  
  
-   [My 用クラス ライブラリのデザイン](#designing)  
  
-   [拡張機能のパッケージ化と配置](#packaging)  
  
##  <a name="customizing"></a> 既存の My 名前空間メンバーのカスタマイズ  
 Visual Basic の `My` 名前空間は、使用しているアプリケーション、コンピューターなどに関して頻繁に使用される情報を公開します。  `My` 名前空間内のオブジェクトの一覧については、「[My Reference](../../../visual-basic/language-reference/keywords/my-reference.md)」を参照してください。  アプリケーションのニーズに合うように、`My` 名前空間の既存のメンバーをカスタマイズすることが必要になる場合があります。  読み取り専用でない、`My` 名前空間のオブジェクトのプロパティは、カスタム値に設定できます。  
  
 たとえば、`My.User` オブジェクトを頻繁に使用して、アプリケーションを実行しているユーザーの現在のセキュリティ コンテキストにアクセスするとします。  しかし、会社では社内ユーザーにその他の情報と機能を公開するために、カスタム ユーザー オブジェクトを使用しています。  このような場合は、次の例に示すように、`My.User.CurrentPrincipal` プロパティの既定値を独自のカスタム プリンシパル オブジェクトのインスタンスに置き換えることができます。  
  
 [!code-vb[VbVbcnExtendingMy#1](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/VisualBasic/extending-the-my-namespace_1.vb)]  
  
 `My.User` オブジェクトの `CurrentPrincipal` プロパティを設定すると、アプリケーションを実行する ID が変更されます。  すると、`My.User` オブジェクトは、新たに指定されたユーザーに関する情報を返します。  
  
##  <a name="addingtoobjects"></a> My オブジェクトへのメンバーの追加  
 `My.Application` および `My.Computer` から返される型は、`Partial` クラスとして定義されます。  したがって、`My.Application` オブジェクトと `My.Computer` オブジェクトは、`MyApplication` または `MyComputer` という `Partial` クラスを作成すると拡張できます。  このクラスは `Private` クラスにはできません。  このクラスを `My` 名前空間の一部として指定した場合、`My.Application` オブジェクトまたは `My.Computer` オブジェクトと共に含まれるプロパティおよびメソッドを追加できます。  
  
 たとえば、次の例では、`DnsServerIPAddresses` というプロパティを `My.Computer` オブジェクトに追加しています。  
  
 [!code-vb[VbVbcnExtendingMy#2](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/VisualBasic/extending-the-my-namespace_2.vb)]  
  
##  <a name="addingcustom"></a> My 名前空間へのカスタム オブジェクトの追加  
 `My` 名前空間には、多くの一般的なプログラミング タスクへのソリューションが用意されていますが、`My` 名前空間で対処していないタスクもあります。  たとえば、アプリケーションがユーザー データ用のカスタム ディレクトリ サービスにアクセスしたり、Visual Basic では既定でインストールされないアセンブリを使用したりすることがあります。  `My` 名前空間を拡張して、一般的なタスクのために、使用している環境に固有なカスタム ソリューションを含めることができます。  `My` 名前空間の拡張は簡単で、増大するアプリケーションのニーズに見合うように新しいメンバーを追加できます。  また、自分で作成した `My` 名前空間の拡張機能を、Visual Basic テンプレートとして他の開発者用に配置できます。  
  
###  <a name="addingtonamespace"></a> My 名前空間へのメンバーの追加  
 `My` は、他の名前空間と同様の名前空間であるため、モジュールを追加して `My` の `Namespace` を指定するだけで、トップ レベルのプロパティを追加できます。  次の例に示すように、このモジュールに `HideModuleName` 属性を注釈として付けます。  `HideModuleName` 属性によって、IntelliSense は `My` 名前空間のメンバーを表示するときに、モジュール名を表示しなくなります。  
  
 [!code-vb[VbVbcnExtendingMy#3](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/VisualBasic/extending-the-my-namespace_3.vb)]  
  
 メンバーを `My` 名前空間に追加するには、必要に応じてモジュールにプロパティを追加します。  `My` 名前空間に追加されるプロパティごとに、`ThreadSafeObjectProvider(Of T)` 型のプライベート フィールドを追加します。この型は、カスタム プロパティによって返される型です。  このフィールドは、`GetInstance` メソッドの呼び出しによってプロパティから返されるスレッド セーフなオブジェクト インスタンスの作成に使用されます。  その結果、拡張プロパティにアクセスする各スレッドは、返された型の独自のインスタンスを受け取ります。  次の例では、`SampleExtension` 型の `SampleExtension` というプロパティを `My` 名前空間に追加します。  
  
 [!code-vb[VbVbcnExtendingMy#4](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/VisualBasic/extending-the-my-namespace_4.vb)]  
  
##  <a name="addingevents"></a> カスタム My オブジェクトへのイベントの追加  
 `My.Application` オブジェクトを使用すると、`My` 名前空間の `MyApplication` 部分クラスを拡張することによって、カスタム `My` オブジェクト用のイベントを公開できます。  Windows ベースのプロジェクトの場合、**ソリューション エクスプローラー**でプロジェクトの **\[My Project\]** ノードをダブルクリックすることができます。  Visual Basic の**プロジェクト デザイナー**では、`Application` タブをクリックして `View Application Events` ボタンをクリックします。  ApplicationEvents.vb という名前の新しいファイルが作成されます。  このファイルには、`MyApplication` クラスを拡張するための次のコードが収められています。  
  
 [!code-vb[VbVbcnExtendingMy#5](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/VisualBasic/extending-the-my-namespace_5.vb)]  
  
 作成したカスタム `My` オブジェクトには、`MyApplication` クラスにカスタム イベント ハンドラーを追加することによって、イベント ハンドラーを追加できます。  カスタム イベントを使用すると、イベント ハンドラーが追加または削除されたとき、あるいはイベントが発生したときに実行されるコードを追加できます。  カスタム イベント用の `AddHandler` コードは、ユーザーがイベントを処理するためにコードを追加した場合にだけ実行します。  たとえば、前のセクションで説明した `SampleExtension` オブジェクトに `Load` イベントがあり、これにカスタム イベント ハンドラーを追加するとします。  次のコード例は、`My.SampleExtension.Load` イベントの発生時に呼び出される、`SampleExtensionLoad` という名前のカスタム イベント ハンドラーを示しています。  新しい `My.SampleExtensionLoad` イベントを処理するためにコードが追加されると、このカスタム イベント コードの `AddHandler` 部分が実行されます。  `MyApplication_SampleExtensionLoad` メソッドは、`My.SampleExtensionLoad` イベントを処理するイベント ハンドラーの例を示すためにこのコード例に含まれています。  `SampleExtensionLoad` イベントは、ApplicationEvents.vb ファイルの編集中にコード エディターの上にある左側のドロップダウン リストで **\[My Application イベント\]** オプションを選択すると使用可能になります。  
  
 [!code-vb[VbVbcnExtendingMy#6](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/VisualBasic/extending-the-my-namespace_6.vb)]  
  
##  <a name="design"></a> デザイン ガイドライン  
 `My` 名前空間に拡張機能を開発するときは、以下のガイドラインを守って、拡張コンポーネントの保守コストが最少になるようにします。  
  
-   **拡張機能のロジックだけを含めるようにする。** `My` 名前空間の拡張機能に含まれるロジックには、`My` 名前空間に必要な機能を公開するために必要とされるコードだけが含まれるようにします。  拡張機能はソース コードとしてユーザー プロジェクトに存在するため、拡張コンポーネントを更新すると保守コストが上昇するので、可能な限り避けてください。  
  
-   **プロジェクトの前提を最小にする。** `My` 名前空間の拡張機能を作成するときは、参照のセット、プロジェクト レベルのインポート、または特定のコンパイラの設定 \(たとえば `Option Strict` をオフにするなど\) を前提としないようにします。  依存関係を最小にし、`Global` キーワードを使用してすべての型参照を完全修飾します。  また、`Option Strict` をオンにして拡張機能をコンパイルするようにし、拡張機能のエラーを最少にとどめます。  
  
-   **拡張コードを分離する。**コードを 1 つのファイルにまとめると、拡張機能は Visual Studio の項目テンプレートとして簡単に配置できるようになります。  詳細については、このトピックの「拡張機能のパッケージ化と配置」を参照してください。  また、`My` 名前空間の拡張コードをすべて 1 つのファイルにまとめるかプロジェクト内の別個のフォルダーに入れると、ユーザーにとって `My` 名前空間の拡張機能が探しやすくなります。  
  
##  <a name="designing"></a> My 用クラス ライブラリのデザイン  
 ほとんどのオブジェクト モデルの場合と同様に、`My` 名前空間に適合するデザイン パターンと、そうでないデザイン パターンがあります。  `My` 名前空間の拡張機能をデザインするときは、以下の原則を考慮してください。  
  
-   **ステートレス メソッド。** `My` 名前空間の各メソッドには、特定のタスクに対する完全なソリューションが用意されている必要があります。  メソッドに渡されるパラメーター値によって、特定のタスクを完了させるために必要な入力がすべて行われるようにしてください。  リソースに対して開かれている接続など、前の状態に依存するメソッドは作成しないようにします。  
  
-   **グローバル インスタンス。** `My` 名前空間で保持される唯一の状態は、プロジェクトに対してグローバルです。  たとえば、`My.Application.Info` は、アプリケーション全体で共有される状態をカプセル化します。  
  
-   **単純なパラメーター型。**複雑なパラメーター型は避け、簡単にします。  パラメーター入力を受け取らないメソッドや、文字列型、プリミティブ型など、簡単な入力型を受け取るメソッドを作成します。  
  
-   **ファクトリ メソッド。**どのようにしてもインスタンス化が困難な型があります。  `My` 名前空間の拡張機能としてファクトリ メソッドを用意すると、この種の型をより簡単に探して使用できます。  効果的なファクトリ メソッドの例として、`My.Computer.FileSystem.OpenTextFileReader` が挙げられます。  .NET Framework ではいくつかのストリーム型を使用できます。  テキスト ファイルを具体的に指定すると、`OpenTextFileReader` によって、ユーザーはどのストリームを使用すればよいかがわかりやすくなります。  
  
 上記のガイドラインは、クラス ライブラリの一般的なデザインの原則を排除するものではありません。  むしろこれらは、Visual Basic および `My` 名前空間を使用する開発者に最も適した推奨事項であるといえます。  クラス ライブラリを作成する際の一般的なデザインの原則については、「[Framework デザイン ガイドライン](../Topic/Framework%20Design%20Guidelines.md)」を参照してください。  
  
##  <a name="packaging"></a> 拡張機能のパッケージ化と配置  
 `My` 名前空間の拡張機能は、Visual Studio のプロジェクト テンプレートに含める方法と、拡張機能をパッケージ化して Visual Studio の項目テンプレートとして配置する方法があります。  `My` 名前空間の拡張機能を Visual Studio の項目テンプレートとしてパッケージ化すると、Visual Basic が持つその他の機能を活用できます。  これらの諸機能を使用すると、プロジェクトが特定のアセンブリを参照するときに拡張機能を含めたり、ユーザーが Visual Basic プロジェクト デザイナーの **\[マイ拡張\]** ページを使用して、`My` 名前空間の拡張機能を明示的に追加したりできます。  
  
 `My` 名前空間の拡張機能の配置方法の詳細については、「[Packaging and Deploying Custom My Extensions](../../../visual-basic/developing-apps/customizing-extending-my/packaging-and-deploying-custom-my-extensions.md)」を参照してください。  
  
## 参照  
 [Packaging and Deploying Custom My Extensions](../../../visual-basic/developing-apps/customizing-extending-my/packaging-and-deploying-custom-my-extensions.md)   
 [Extending the Visual Basic Application Model](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)   
 [Customizing Which Objects are Available in My](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)   
 [\[マイ拡張\] ページ \(プロジェクト デザイナー\)](/visual-studio/ide/reference/my-extensions-page-project-designer-visual-basic)   
 [\[アプリケーション\] ページ \(プロジェクト デザイナー\) \(Visual Basic\)](/visual-studio/ide/reference/application-page-project-designer-visual-basic)   
 [Partial](../../../visual-basic/language-reference/modifiers/partial.md)