---
title: "WCF のテスト用クライアント (WcfTestClient.exe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d4302855-677f-4640-aa90-c5d785d72fb7
caps.latest.revision: "45"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 28098a4e598d1c3bede3b05e3afe1001c3944d42
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="wcf-test-client-wcftestclientexe"></a>WCF のテスト用クライアント (WcfTestClient.exe)
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] テスト クライアント (WcfTestClient.exe) は、テスト パラメーターを入力し、その入力をサービスに送信して、サービスから返される応答を確認できる GUI ツールです。 このツールを [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス ホストと組み合わせて使用すると、シームレスにサービスをテストできるようになります。  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Test Client (WcfTestClient.exe) は、C:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\ にあります。  
  
## <a name="scenarios-for-using-test-client"></a>テスト用クライアントを使用するシナリオ  
 以下のセクションで、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] のテスト用クライアントを使用して開発プロセスを効率化できる最も一般的なシナリオについて説明します。  
  
### <a name="inside-visual-studio"></a>Visual Studio 内  
  
#### <a name="wcf-service-host-starts-wcf-test-client-with-a-single-service"></a>WCF サービス ホストが、1 つのサービスを使用する WCF のテスト用クライアントを開始する  
 新しい [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス プロジェクトを作成し、F5 キーを押してデバッガーを起動すると、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス ホストがプロジェクトのサービスのホストを開始します。 その後、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] のテスト用クライアントが開き、構成ファイルに定義されているサービス エンドポイントの一覧が表示されます。 ユーザーは、パラメーターをテストしてサービスを呼び出すことができ、このプロセスを繰り返して、サービスのテストおよび検証を継続的に行うことができます。  
  
#### <a name="wcf-service-host-starts-wcf-test-client-with-multiple-services"></a>WCF サービス ホストが、複数のサービスを使用する WCF のテスト用クライアントを開始する  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] テスト クライアントは、複数のサービスを含むサービス プロジェクトをデバッグするためにも使用できます。 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] のテスト用クライアントは、開始されると、自動的にプロジェクトのサービスのリストを反復処理し、テストするためにそれらを開きます。  
  
### <a name="outside-visual-studio"></a>Visual Studio の外部  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] テスト クライアント (WcfTestClient.exe) を Visual Studio の外部で呼び出して、インターネット上の任意のサービスをテストすることもできます。 このツールを見つけるには、次の場所に移動します。  
  
 C:\Program Files\Microsoft Visual Studio 9.0\Common7\IDE\  
  
 ツールを使用するには、ファイル名をダブルクリックしてこの場所からツールを開くか、コマンド ラインからツールを起動します。  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] テスト クライアントは、任意の数の URI をコマンド ライン引数として受け取ります。  これらの引数には、テストできるサービスの URI を指定します。  
  
 `wcfTestClient.exe URI1 URI2 …`  
  
 後に、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]テスト用クライアント ウィンドウを開くと、をクリックして**ファイル**->**サービスの追加**、開きたいサービスのエンドポイント アドレスを入力します。  
  
## <a name="wcf-test-client-user-interface"></a>WCF のテスト用クライアントのユーザー インターフェイス  
 1 つのサービスまたは複数のサービスを使用する [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] のテスト用クライアントを使用できます。  
  
### <a name="service-operations"></a>サービス操作  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] のテスト用クライアントのメイン ウィンドウの左ペインには、使用できるすべてのサービスが、それぞれのエンドポイントおよび操作と共に表示されます。  
  
 操作をダブルクリックすると、その操作の名前が付いた新しいタブ内の右ペインで、操作の内容を表示できます。  
  
 左ペインには、クライアントの構成ファイルも表示されます。 いずれかの項目をダブルクリックすると、右ペインの新しいタブ付きウィンドウにファイルの内容が表示されます。  
  
### <a name="entering-test-parameters"></a>テスト パラメーターの入力  
 テスト パラメーターを表示するには、右ペインで操作をダブルクリックして開きます。 パラメーターを示す**表示書式**既定では、表示され、サービスをテスト パラメーターに任意の値を入力できます。  
  
 表示するには、メッセージの XML をクリックして**XML**です。 それらをサービスに送信する をクリックして**Invoke**です。  
  
 データセット パラメーターをクリックして、**しています.** ボタンの横に**を編集しています.** データ グリッドを表示する新しいウィンドウで編集します。 外観に注意してください、 **DataSet のコピー**と**貼り付けデータセット**ボタン。 最初の編集時に DataSet オブジェクトのスキーマが不明の場合、DataGrid は空になります。 スキーマが同じ DataSet オブジェクトを DataGrid の現在のオブジェクトに貼り付ける必要があります  (スキーマは、貼り付け操作の前に別の場所からコピーする必要があります)。クリックして、将来の使用量のデータセット オブジェクトをコピーすることも、 **DataSet のコピー**ボタンをクリックします。  
  
 サービスの応答がテスト パラメーターの下に表示されます。  
  
> [!NOTE]
>  想定される戻り値が文字列の場合、入力が引用符で囲まれていなくても、結果は引用符で囲まれた文字列として表示されます。  
  
 サービスのコントラクトの作成時に特定の操作を一方向として指定した場合は、サービスの応答は表示されません。 メッセージが配信のキューに置かれると、メッセージが正常に送信されたことを通知するダイアログ ボックスがすぐに表示されます。  
  
### <a name="session-support"></a>セッション サポート  
 **新しいプロキシを開始**サービス操作のタブでチェック ボックスでは、セッション サポートを切り替えることができます。 既定では、このチェック ボックスはオフになります。  
  
 特定の操作 (または同じサービス エンドポイントの別の操作) のテスト パラメーターを入力し、をクリックして**Invoke**複数回チェック ボックスをオフになって、これらの操作が 1 つのプロキシを共有し、サービスの状態が複数の操作には、永続化されます。  
  
 場合、**新しいプロキシを開始** チェック ボックスをオンになって、新しいプロキシが開始された各**Invoke**、前のセッション シナリオが終了すると、およびサービスの状態をリセットします。  
  
### <a name="editing-client-configuration"></a>クライアント構成の編集  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] のテスト用クライアントのメイン ウィンドウの左ペインには、クライアントの構成ファイルが表示されます。 いずれかの項目をダブルクリックすると、右ペインにファイルの内容が表示されます。  
  
#### <a name="edit-with-service-configuration-editor"></a>サービス構成エディターを使用した編集  
 右クリック**Config ファイル**、左側のウィンドウ クリックし、コンテキスト メニューで**SvcConfigEditor で編集**です。 サービス構成エディターが起動し、クライアント構成の内容が表示されます。 このツール内で構成を編集して保存できます。  
  
 サービス構成エディターでファイルを保存すると、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] テスト クライアントでは、ファイルが外部で変更されたことを通知する警告メッセージが表示され、ファイルを再度読み込むかどうかをたずねられます。  
  
 選択した場合**はい**、[Client.dll.config] タブで設定内容がエディターで行った変更を反映します。  
  
 選択した場合**いいえ**の構成 [Client.dll.config] タブの内容が変更されない、および変更されたコンテンツは自動的にソース ファイルに保存します。  
  
#### <a name="restore-to-default-configuration"></a>既定の構成への復元  
 すべての変更をキャンセルし、既定のクライアント構成に復元を右クリックしたい場合**Config ファイル**、左側のウィンドウ クリックし、コンテキスト メニューで**既定の構成に復元**です。既定の構成値が読み込まれ、[Client.dll.config] タブの内容を復元します。  
  
#### <a name="validate-changes"></a>変更の検証  
 保存した変更が [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] テスト クライアントに読み込まれると、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] スキーマに対して構成の有効性のチェックが行われます。 エラーが見つかった場合は、エラーの詳細を示すダイアログ ボックスが表示されます。  
  
 プロキシの生成は、バイナリのコンパイル中、またはサービスの呼び出し、中に (つまり、および「... の編集」、「復元...」) の編集をサポートするメニュー項目が無効になります。 更新された構成が [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] テスト クライアントに読み込まれるときは、サービスの呼び出しも無効になります。  
  
#### <a name="persist-client-configuration"></a>クライアント構成の保持  
 **ツール**->**オプション**->**クライアント構成** タブには、**常に再生成の構成時に起動します。サービス**オプションは、既定で有効にします。 このチェック ボックスがオンの場合は、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] テスト クライアントによってサービスが読み込まれるたびに、最新のサービス コントラクトとサービスの App.config ファイルに基づいて構成ファイルが再生成されます。  
  
 クライアントの構成を編集している場合、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]サービスとサービスのデバッグを常に、この更新ファイルを使用する場合は、ボックスをオフに、**を再生成**オプション。 このようにすると、サービスを更新して [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] テスト クライアントを再び開いた場合でも、Client.dll.config ファイルとして使用されるのは、更新されたサービスに基づいて再生成されたファイルではなく、以前に更新したファイルになります。  
  
 ただし、再生成されたプロキシとの一貫性を保つために、構成ファイルの編集が必要になる場合があります。 サービスを更新したことが原因で、再生成されたプロキシと構成ファイルが一致しなくなると、サービスを呼び出したときにエラーが発生します。  
  
> [!CAUTION]
>  変更したクライアント構成ファイルを後で再利用することにした場合、該当するファイルは次の場所で見つけることができます。  
>   
>  \Documents and 設定\\\My Documents\Test クライアント プロジェクトの [ユーザー アカウント]。  
>   
>  クライアント構成ファイルに格納されている更新された資格情報は、このフォルダーのアクセス制御リスト (ACL) によって保護されています。  
  
### <a name="adding-removing-and-refreshing-services"></a>サービスの追加、削除、および更新  
  
#### <a name="add-service"></a>サービスの追加  
 をクリックして**ファイル**->**サービスの追加**にサービスを追加する[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]テスト クライアントです。 次に、追加するサービスの URI (エンドポイント アドレス) を入力する必要があります。 サービスのアドレスには、MEX アドレスまたは WSDL アドレスを指定できます。  
  
 10 の最近追加されたサービスのエンドポイントの一覧を見つけることもできます、**最近サービス**サブメニュー。 いずれかをクリックすると、選択したサービスが [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] テスト クライアントに追加されます。  
  
 また、サービスのツリーのルートを右クリックすることもできます。**マイ サービス プロジェクト**、を選択し**サービスの追加**に同じ結果を実現します。  
  
 プロキシの生成中、バイナリのコンパイル中、またはサービスの呼び出し中は、サービスの追加をサポートするメニュー項目が無効になります。 また、サービスの呼び出しも無効になります。  
  
#### <a name="remove-service"></a>サービスの削除  
 削除して、選択するサービスのサービス ルートを右クリックして**サービスの削除**からサービスを削除する[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]テスト クライアントです。  
  
 プロキシの生成中、バイナリのコンパイル中、またはサービスの呼び出し中は、サービスの削除をサポートするメニュー項目が無効になります。 また、サービスの呼び出しも無効になります。  
  
#### <a name="refresh-service"></a>サービスの更新  
 中にサービスへの変更が行われた場合[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]テスト クライアントが実行されていていることを確認する、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]そのサービスの実装をテスト用クライアントが最新では、サービスのサービス ルートを右クリックし **更新サービス**です。 更新後、サービスの状態はリセットされます。  
  
 プロキシの生成中、バイナリのコンパイル中、またはサービスの呼び出し中は、サービスの更新をサポートするメニュー項目が無効になります。 また、サービスの呼び出しも無効になります。  
  
## <a name="location-of-files-generated-by-the-test-client"></a>テスト クライアントが生成するファイルの場所  
 既定では、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]テスト クライアントによって生成されたクライアント コードと構成ファイルは"%appdata%\Local\temp\Test Client Projects"フォルダーです。 このフォルダーは、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] テスト クライアントの終了後に削除されます。 構成ファイルが変更された場合[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]テスト クライアント、および**常に再生成 Config サービスの起動時**オプションが無効になっている、変更されたファイルは"My Documents\Test"キャッシュ Config"フォルダーにコピークライアント プロジェクト Documents\Test Client Projects"のマッピング (メタデータのアドレスの名前へのファイルの) XML ファイルをインデックスとして使用します。  
  
 コマンド ラインから [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] テスト クライアントを起動し、`/ProjectPath` スイッチを使用して、生成されたファイルを格納する新しいパスを指定することもできます。また、`/RestoreProjectPath` スイッチを使用して、既定の場所を復元することもできます。 構文は次のとおりです。  
  
 `wcfTestClient.exe /ProjectPath [desired location]`  
  
 このコマンドを実行しても、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] テスト クライアントは開きません。 フォルダーの場所が変更されるだけです。 このコマンドは、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] テスト クライアントが実行されているかどうかにかかわらず実行できます。 新しい場所は、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] テスト クライアントが再起動したときに適用されます。 場所の情報は、レジストリか、"%appdata%\Local\temp\Test Client Projects"フォルダーの WcfTestClient.exe.option ファイルに保存できます。  
  
## <a name="features-supported-by-wcf-test-client"></a>WCF のテスト用クライアントでサポートされる機能  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] テスト クライアントがサポートする機能を次に示します。  
  
-   サービスの呼び出し : 要求/応答メッセージおよび一方向メッセージ  
  
-   バインディング : Svcutil.exe でサポートされるすべてのバインディング  
  
-   セッションの制御  
  
-   メッセージ コントラクト  
  
-   XML シリアル化  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] テスト クライアントでサポートされない機能を次に示します。  
  
-   型: <xref:System.IO.Stream>、<xref:System.ServiceModel.Channels.Message>、<xref:System.Xml.XmlElement>、<xref:System.Xml.XmlAttribute>、<xref:System.Xml.XmlNode>、<xref:System.Xml.Serialization.IXmlSerializable> インターフェイスを実装する型 (関連する <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> 属性を含む)、<xref:System.Xml.Linq.XDocument> 型と <xref:System.Xml.Linq.XElement> 型、および ADO.NET <xref:System.Data.DataTable> 型。  
  
-   双方向コントラクト  
  
-   トランザクション  
  
-   セキュリティ : [!INCLUDE[infocard](../../../includes/infocard-md.md)]、証明書、およびユーザー名/パスワード  
  
-   バインディング : WSFederationBinding、任意のコンテキスト バインディングおよび HTTPS バインディング、WebHttpBinding (JSON 応答メッセージ サポート)  
  
## <a name="closing-wcf-test-client"></a>WCF のテスト用クライアントの終了  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] のテスト用クライアントは、次の方法で閉じることができます。  
  
-   **ファイル** メニューのをクリックして**終了**です。 代わりに、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]テスト クライアントのメイン ウィンドウ、をクリックして**閉じる**です。 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] テスト クライアントが [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] によって起動された場合は、どちらの手順でも [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービスの自動ホストがシャットダウンし、[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] のデバッグ処理が停止します。  
  
-   右クリックし、 **WCF サービス ホスト**をクリックして通知領域アイコン**終了します。** これにより、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービスの自動ホストと [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] のテスト用クライアントの両方がシャットダウンし、[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] のデバッグ処理が停止します。  
  
## <a name="see-also"></a>参照  
 [WCF サービス ホスト (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
