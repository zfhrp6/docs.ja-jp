---
title: "メッセージ クラスの使用 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d1d62bfb-2aa3-4170-b6f8-c93d3afdbbed
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# メッセージ クラスの使用
<xref:System.ServiceModel.Channels.Message>クラスは基本となる[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]します。 クライアントとサービス間のすべての通信が最終的な結果に<xref:System.ServiceModel.Channels.Message>インスタンスが送受信されました。  
  
 対話することはない通常の<xref:System.ServiceModel.Channels.Message>クラスを直接します。 その代わりに、データ コントラクト、メッセージ コントラクト、操作コントラクトなどの [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービス モデル コントラクトを使用して送受信メッセージを表します。 ただし、いくつか高度なシナリオを使用してプログラミングすることができます、<xref:System.ServiceModel.Channels.Message>クラスを直接します。 使用するなど、<xref:System.ServiceModel.Channels.Message>クラス。  
  
-   [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] オブジェクトをシリアル化する以外の方法で送信メッセージの内容を作成する必要がある場合 (ディスク上のファイルからメッセージを直接作成する場合など)。  
  
-   [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] オブジェクトに逆シリアル化する以外の方法で受信メッセージの内容を使用する必要がある場合 (XSLT 変換を XML の未処理コンテンツに適用する場合など)。  
  
-   メッセージ コンテンツに関係なく、一般的な方法でメッセージを処理する必要がある場合 (メッセージをルーティングまたは転送する場合や、ルーターシステム、負荷分散システム、または発行/定期受信システムを構築する場合など)。  
  
 使用する前に、<xref:System.ServiceModel.Channels.Message>クラス、理解しておく、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]のデータ転送アーキテクチャ[データ転送のアーキテクチャ概要](../../../../docs/framework/wcf/feature-details/data-transfer-architectural-overview.md)します。  
  
 A<xref:System.ServiceModel.Channels.Message>は、データの汎用的なコンテナーですが、その設計は SOAP プロトコル メッセージのデザインとほとんど同じです。 SOAP と同様に、メッセージには本文とヘッダーの両方があります。 メッセージ本文には実際のペイロード データが格納され、ヘッダーには追加の名前付きデータ コンテナーが格納されます。 本文とヘッダーの読み書きルールは異なります。たとえば、ヘッダーは必ずメモリにバッファーされるので順序や回数に関係なくアクセスできますが、本文は&1; 度だけ読み取ってストリーミングできます。 通常 SOAP を使用する場合、メッセージ本文は SOAP 本文にマップされ、メッセージ ヘッダーは SOAP ヘッダーにマップされます。  
  
## <a name="using-the-message-class-in-operations"></a>処理におけるメッセージ クラスの使用  
 使用することができます、<xref:System.ServiceModel.Channels.Message>処理、操作のいずれかまたは両方の戻り値の入力パラメーターとしてクラスです。 場合<xref:System.ServiceModel.Channels.Message>使用は任意の場所演算では、次の制限を適用します。  
  
-   処理に `out` パラメーターまたは `ref` パラメーターを含めることはできません。  
  
-   複数の `input` パラメーターを指定できません。 パラメーターがある場合は、そのパラメーターを Message 型またはメッセージ コントラクト型にする必要があります。  
  
-   戻り値の型は、`void` 型、`Message` 型、またはメッセージ コントラクト型にする必要があります。  
  
 有効な操作コントラクトを次のコード例に示します。  
  
 [!code-csharp[C_UsingTheMessageClass#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#1)]
 [!code-vb[C_UsingTheMessageClass#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#1)]  
  
## <a name="creating-basic-messages"></a>基本メッセージの作成  
 <xref:System.ServiceModel.Channels.Message>クラスには静的`CreateMessage`ファクトリ メソッド基本的なメッセージを作成することができます。  
  
 すべて`CreateMessage`型のバージョン パラメーターを受け取るオーバー ロード<xref:System.ServiceModel.Channels.MessageVersion>メッセージで使用する SOAP と Ws-addressing のバージョンを示します。 受信メッセージと同じプロトコル バージョンを使用する場合は、使用、 <xref:System.ServiceModel.OperationContext.IncomingMessageVersion%2A>プロパティを<xref:System.ServiceModel.OperationContext>から取得したインスタンス、<xref:System.ServiceModel.OperationContext.Current%2A>プロパティです。 また、ほとんどの `CreateMessage` オーバーロードには、メッセージで使用する SOAP アクションを示す文字列パラメーターもあります。 バージョンを `None` に設定すると、SOAP エンベロープの生成を無効にできます。この場合、メッセージは本文のみで構成されます。  
  
## <a name="creating-messages-from-objects"></a>オブジェクトからのメッセージの作成  
 最も基本的な `CreateMessage` オーバーロードは、バージョンとアクションだけを受け取り、本文が空のメッセージを作成します。 別のオーバー ロードは、追加<xref:System.Object>パラメーターの場合、メッセージ本体を持つ指定したオブジェクトのシリアル化表現は、これが作成されます。 使用して、 <xref:System.Runtime.Serialization.DataContractSerializer>シリアル化の既定の設定にします。 異なるシリアライザーを使用する場合、または `DataContractSerializer` の構成を変更する場合は、`CreateMessage` パラメーターも受け取る `XmlObjectSerializer` オーバーロードを使用します。  
  
 たとえば、メッセージにオブジェクトを返す場合は、次のコードを使用できます。  
  
 [!code-csharp[C_UsingTheMessageClass#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#2)]
 [!code-vb[C_UsingTheMessageClass#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#2)]  
  
## <a name="creating-messages-from-xml-readers"></a>XML リーダーからのメッセージの作成  
 ある`CreateMessage`を受け取るオーバー ロード、 <xref:System.Xml.XmlReader>または<xref:System.Xml.XmlDictionaryReader>オブジェクトではなく、本文のです。 この場合、メッセージの本文には、渡された XML リーダーから読み取られた XML が格納されます。 たとえば、次のコードは、XML ファイルから読み取られた内容を本文に持つメッセージを返します。  
  
 [!code-csharp[C_UsingTheMessageClass#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#3)]
 [!code-vb[C_UsingTheMessageClass#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#3)]  
  
 さらに、ある`CreateMessage`を受け取るオーバー ロード、 <xref:System.Xml.XmlReader>または<xref:System.Xml.XmlDictionaryReader>メッセージ全体と、本文だけでなくを表します。 これらのオーバーロードは、整数の `maxSizeOfHeaders` パラメーターも受け取ります。 メッセージが作成されると直ちにヘッダーがメモリに必ずバッファーされます。このパラメーターは、発生するバッファーの量を制限します。 XML が信頼できないソースから取り込まれる場合は、このパラメーターを安全な値に設定してサービス拒否攻撃の可能性を軽減することが重要です。 XML リーダーが表す、メッセージの SOAP バージョンと WS-Addressing バージョンは、バージョン パラメーターを使用して示されるバージョンと一致する必要があります。  
  
## <a name="creating-messages-with-bodywriter"></a>BodyWriter によるメッセージの作成  
 `CreateMessage` オーバーロードの&1; つには、メッセージ本文を記述するための `BodyWriter` インスタンスを受け取るものがあります。 `BodyWriter` は、メッセージ本文の作成方法をカスタマイズするために派生させることのできる抽象クラスです。 独自の `BodyWriter` 派生クラスを作成すると、カスタマイズした方法でメッセージ本文を記述できます。 オーバーライドする必要があります、`BodyWriter.OnWriteBodyContents`を受け取るメソッド、 <xref:System.Xml.XmlDictionaryWriter>; このメソッドは、本文の作成を担当します。  
  
 本文ライターでは、バッファリングを行うことも、行わないようにする (ストリームする) こともできます。 バッファリングされる本文ライターでは、その内容を何度でも出力できますが、ストリームされる本文ライターの内容は&1; 度しか出力できません。 `IsBuffered` プロパティは、本文ライターがバッファリングされるかどうかを示します。 独自の本文ライターでこれを設定するには、ブール型の `BodyWriter` パラメーターを受け取る `isBuffered` プロテクト コンストラクターを呼び出します。 本文ライターでは、バッファリングされない本文ライターから、バッファリングされた本文ライターを作成することがサポートされています。 `OnCreateBufferedCopy` メソッドをオーバーライドすると、この処理をカスタマイズできます。 既定では、`OnWriteBodyContents` から返された XML が格納されているメモリ内のバッファーが使用されます。 `OnCreateBufferedCopy` は、整数の `maxBufferSize` パラメーターを受け取ります。このメソッドをオーバーライドする場合は、この最大サイズを超えるバッファーを作成しないようにする必要があります。  
  
 `BodyWriter` クラスには、`WriteBodyContents` メソッドと `CreateBufferedCopy` メソッドが用意されています。基本的にこれらは、それぞれ `OnWriteBodyContents` メソッドと `OnCreateBufferedCopy` メソッドの薄いラッパー (thin wrapper) です。 これらのメソッドは、バッファリングされない本文ライターが&2; 回以上アクセスされないように状態チェックを実行します。 これらのメソッドは、`Message` に基づいたカスタム `BodyWriters` 派生クラスを作成する場合にのみ直接呼び出されます。  
  
## <a name="creating-fault-messages"></a>エラー メッセージの作成  
 特定の `CreateMessage` オーバーロードを使用して SOAP エラー メッセージを作成できます。 これらはの最も基本的な<xref:System.ServiceModel.Channels.MessageFault>エラーを説明するオブジェクト。 他のオーバーロードは、利便性のために用意されています。 このようなオーバーロードの&1; つは、`FaultCode` と理由の文字列を受け取り、その情報を `MessageFault` で使用して `MessageFault.CreateFault` を作成します。 他のオーバーロードは、詳細オブジェクトを受け取り、そのオブジェクトをエラー コードと理由と共に `CreateFault` に渡します。 たとえば、次の操作はエラーを返します。  
  
 [!code-csharp[C_UsingTheMessageClass#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#4)]
 [!code-vb[C_UsingTheMessageClass#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#4)]  
  
## <a name="extracting-message-body-data"></a>メッセージ本文データの抽出  
 `Message` クラスでは、その本文から情報を抽出する複数の方法がサポートされています。 方法は次のカテゴリに分類されます。  
  
-   XML ライターに&1; 度に書き込まれるメッセージ本文全体の取得。 これとして参照は*メッセージを書き込む*します。  
  
-   メッセージ本文での XML リーダーの取得。 これにより、必要に応じてメッセージ本文に後で少しずつアクセスできます。 これとして参照は*メッセージの読み取り*します。  
  
-   メモリ内のバッファーには、本文を含むメッセージ全体をコピーできます、 <xref:System.ServiceModel.Channels.MessageBuffer>型です。 これとして参照は*メッセージのコピー*します。  
  
 `Message` の本文には、アクセス方法に関係なく&1; 回しかアクセスできません。 メッセージ オブジェクトには `State` プロパティがあります。このプロパティは Created として初期化されます。 この状態は、前の&3; つのアクセス方法により、それぞれ Written、Read、Copied に設定されます。 また、メッセージ本文の内容が不要になったときは、`Close` メソッドによって状態が Closed に設定されます。 メッセージ本文には、状態が Created の場合にのみアクセスできます。状態が変更された後で Created に戻す方法はありません。  
  
## <a name="writing-messages"></a>メッセージの書き込み  
 <xref:System.ServiceModel.Channels.Message.WriteBodyContents%28System.Xml.XmlDictionaryWriter%29>メソッドの本文の内容を指定された`Message`指定された XML ライターのインスタンス。 <xref:System.ServiceModel.Channels.Message.WriteBody%2A>メソッドは同じで、適切なラッパー要素に、本文の内容を囲む点が異なります (たとえば、 `soap:body`>)。 最後に、 <xref:System.ServiceModel.Channels.Message.WriteMessage%2A> SOAP エンベロープとヘッダーをラップする側を含むメッセージ全体を書き込みます。 SOAP が無効になっている場合 (バージョンが `MessageVersion.None`)、これらの&3; つのメソッドはすべて同じ処理を行います。つまり、メッセージ本文の内容を書き込みます。  
  
 たとえば、次のコードは、受信メッセージの本文をファイルに書き込みます。  
  
 [!code-csharp[C_UsingTheMessageClass#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#5)]
 [!code-vb[C_UsingTheMessageClass#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#5)]  
  
 さらに、特定の SOAP 開始要素タグを書き込む&2; つのヘルパー メソッドがあります。 これらのメソッドはメッセージ本文にアクセスしないため、メッセージの状態は変わりません。 次の設定があります。  
  
-   <xref:System.ServiceModel.Channels.Message.WriteStartBody%2A>など、開始本文要素を書き込みます`<soap:Body>`します。  
  
-   <xref:System.ServiceModel.Channels.Message.WriteStartEnvelope%2A>など、開始エンベロープ要素を書き込みます`<soap:Envelope>`します。  
  
 対応する終了要素タグを書き込むには、対応する XML ライターで `WriteEndElement` を呼び出します。 これらのメソッドが直接呼び出されることはほとんどありません。  
  
## <a name="reading-messages"></a>メッセージの読み取り  
 メッセージ本体を読み取る主な方法は呼び出す<xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A>します。 戻ります、 <xref:System.Xml.XmlDictionaryReader>メッセージ本文の読み取りに使用することできます。 注意してください、<xref:System.ServiceModel.Channels.Message>読み取り状態に遷移するとすぐに<xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A>が呼び出されると、返された XML リーダーを使用する場合にないとします。  
  
 <xref:System.ServiceModel.Channels.Message.GetBody%2A>メソッドでは型指定されたオブジェクトとしてメッセージ本文にアクセスすることもできます。 このメソッドを使用して内部的には、`GetReaderAtBodyContents`にメッセージの状態を移行するため、<xref:System.ServiceModel.Channels.MessageState>状態 (を参照してください、<xref:System.ServiceModel.Channels.Message.State%2A>プロパティ)。  
  
 確認することをお勧めは、 <xref:System.ServiceModel.Channels.Message.IsEmpty%2A>プロパティの場合、メッセージ本文は空と<xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A>スロー、 <xref:System.InvalidOperationException>します。 また、受信したメッセージ (返信など) の場合、することも確認する<xref:System.ServiceModel.Channels.Message.IsFault%2A>メッセージにエラーが含まれるかどうかを示します。  
  
 最も基本的なオーバー ロード<xref:System.ServiceModel.Channels.Message.GetBody%2A>型 (ジェネリック パラメーターで示されます) を使用して、インスタンスにメッセージ本文をシリアル化解除、 <xref:System.Runtime.Serialization.DataContractSerializer>と既定の設定で構成されて、 <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A>クォータが無効になっています。 別のシリアル化エンジンを使用するか、または構成するかどうか、`DataContractSerializer`既定以外の方法で使用して、 <xref:System.ServiceModel.Channels.Message.GetBody%2A>を受け取るオーバー ロード、 <xref:System.Runtime.Serialization.XmlObjectSerializer>します。  
  
 たとえば、次のコードは、シリアル化された `Person` オブジェクトを含むメッセージ本文からデータを抽出し、その人の名前を出力します。  
  
 [!code-csharp[C_UsingTheMessageClass#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#6)]
 [!code-vb[C_UsingTheMessageClass#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#6)]  
  
## <a name="copying-a-message-into-a-buffer"></a>バッファーへのメッセージのコピー  
 場合によっては、メッセージ本文に&2; 回以上アクセスする必要が生じます。たとえば、パブリッシャー/サブスクライバー システムの一部として、同じメッセージを複数の宛先に転送する場合です。 この場合、メッセージ全体 (本文を含む) をメモリ内にバッファーする必要があります。 呼び出すことによってこれを行う<xref:System.ServiceModel.Channels.Message.CreateBufferedCopy%28System.Int32%29>します。 このメソッドは、最大バッファー サイズを表す整数パラメーターを受け取り、このサイズ以下のバッファーを作成します。 信頼されていないソースからメッセージを受信する場合は、これを安全な値に設定することが重要です。  
  
 バッファーとして返される、 <xref:System.ServiceModel.Channels.MessageBuffer>インスタンス。 バッファー内のデータには、いくつかの方法でアクセスできます。 呼び出すことの主な方法です<xref:System.ServiceModel.Channels.Message.CreateMessage%2A>を作成する`Message`バッファーからのインスタンス。  
  
 実装には、バッファー内のデータにアクセスする方法、 <xref:System.Xml.XPath.IXPathNavigable>インターフェイスが、 <xref:System.ServiceModel.Channels.MessageBuffer>クラスを基になる XML に直接アクセスを実装します。 いくつか<xref:System.ServiceModel.Channels.MessageBuffer.CreateNavigator%2A>を作成できるオーバー ロード<xref:System.Xml.XPath>ナビゲーター、ノード クォータで保護されたアクセス可能 XML ノードの数を制限します。 これにより、非常に長い処理時間によるサービス拒否攻撃を防止できます。 このクォータは、既定では無効です。 いくつか`CreateNavigator`XML 内の空白の処理方法を指定できるオーバー ロードを使用して、 <xref:System.Xml.XmlSpace>列挙型の既定値は、`XmlSpace.None`です。  
  
 メッセージ バッファーの内容にアクセスする最後の方法は、その内容を使用してストリームに書き出す<xref:System.ServiceModel.Channels.Message.WriteMessage%2A>します。  
  
 `MessageBuffer` を操作する手順を次の例に示します。受信メッセージを複数の受信者に転送してからファイルに記録します。 バッファリングを行わないと、メッセージの本文には&1; 回しかアクセスできないため、この処理は不可能になります。  
  
 [!code-csharp[C_UsingTheMessageClass#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#7)]
 [!code-vb[C_UsingTheMessageClass#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#7)]  
  
 `MessageBuffer` クラスには、この他にも注目すべきメンバーがあります。 <xref:System.ServiceModel.Channels.MessageBuffer.Close%2A>バッファーの内容が必要な不要になった場合は、リソースを解放メソッドを呼び出すことができます。 <xref:System.ServiceModel.Channels.MessageBuffer.BufferSize%2A>プロパティが割り当てられたバッファーのサイズを返します。 <xref:System.ServiceModel.Channels.MessageBuffer.MessageContentType%2A>プロパティは、メッセージの MIME コンテンツ タイプを返します。  
  
## <a name="accessing-the-message-body-for-debugging"></a>デバッグのためのメッセージ本文へのアクセス  
 呼び出すことができます、デバッグのための<xref:System.ServiceModel.Channels.Message.ToString%2A>メソッドを文字列としてメッセージの表現を取得します。 一般に、メッセージがテキスト エンコーダーでエンコードされていれば、この表現はネットワーク上でのメッセージの表示形式と一致します。ただし、XML の場合は人間にとって読みやすいように書式設定されます。 1 つの例外はメッセージ本文です。 本文は&1; 度しか読み取ることができません。また、`ToString` はメッセージの状態を変更しません。 したがって、`ToString`メソッドを選択し、本文にアクセスできない可能性があります (たとえば、「...」プレース ホルダーを置き換えることがあります "...") で代用されることがあります。 したがって、メッセージ本文の内容が重要な場合は、`ToString` を使用してメッセージを記録しないでください。  
  
## <a name="accessing-other-message-parts"></a>メッセージの他の部分へのアクセス  
 メッセージの本文以外の情報にアクセスするさまざまなプロパティが用意されています。 ただし、これらのプロパティは、メッセージを閉じると呼び出すことができなくなります。  
  
-   <xref:System.ServiceModel.Channels.Message.Headers%2A>プロパティは、メッセージ ヘッダーを表します。 このトピックの後の「ヘッダーの操作」を参照してください。  
  
-   <xref:System.ServiceModel.Channels.Message.Properties%2A>プロパティは、一般に送出されません、メッセージが送信されるときに、メッセージに添付された名前付きのデータの一部であるメッセージのプロパティを表します。 このトピックの後の「プロパティの操作」を参照してください。  
  
-   <xref:System.ServiceModel.Channels.Message.Version%2A>プロパティが、メッセージに関連付けられている SOAP と Ws-addressing のバージョンを示すまたは`None`SOAP が無効になっている場合。  
  
-   <xref:System.ServiceModel.Channels.Message.IsFault%2A>プロパティを返します。`true`メッセージが SOAP エラー メッセージである場合。  
  
-   <xref:System.ServiceModel.Channels.Message.IsEmpty%2A>プロパティを返します。`true`場合は、メッセージが空です。  
  
 使用することができます、 <xref:System.ServiceModel.Channels.Message.GetBodyAttribute%28System.String%2CSystem.String%29>本文のラッパー要素の特定の属性にアクセスする方法 (たとえば、 `<soap:Body>`)、特定の名前と名前空間で識別されます。 このような属性が見つからない場合は、`null` が返されます。 このメソッドは、`Message` の状態が Created の場合 (メッセージ本文がまだアクセスされていない場合) にのみ呼び出すことができます。  
  
## <a name="working-with-headers"></a>ヘッダーの操作  
 A`Message`と呼ばれる、名前付きの XML フラグメントの任意の数を含めることができます*ヘッダー*します。 通常、各フラグメントは SOAP ヘッダーにマップされます。 ヘッダーを使用してアクセスされる、`Headers`型のプロパティ<xref:System.ServiceModel.Channels.MessageHeaders>します。 <xref:System.ServiceModel.Channels.MessageHeaders>のコレクションは、 <xref:System.ServiceModel.Channels.MessageHeaderInfo>を通じてアクセスできるオブジェクト、および個々 のヘッダー、 <xref:System.Collections.IEnumerable>インターフェイスまたはインデクサーです。 たとえば、次のコードでは、`Message` のすべてのヘッダー名を表示します。  
  
 [!code-csharp[C_UsingTheMessageClass#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#8)]
 [!code-vb[C_UsingTheMessageClass#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#8)]  
  
#### <a name="adding-removing-finding-headers"></a>ヘッダーの追加、削除、検索  
 新しいヘッダーを追加するにを使用してすべての既存のヘッダーの最後に、<xref:System.ServiceModel.Channels.MessageHeaders.Add%2A>メソッドです。 使用することができます、<xref:System.ServiceModel.Channels.MessageHeaders.Insert%2A>メソッドを特定のインデックスに、ヘッダーを挿入します。 挿入されたアイテムに応じて既存のヘッダーは移動します。 ヘッダーは、インデックスに従って順序付けられ、使用できる最初のインデックスは 0 です。 ボリュームを使用して、さまざまな<xref:System.ServiceModel.Channels.MessageHeaders.CopyHeadersFrom%2A>を異なるヘッダーを追加するメソッドのオーバー ロード`Message`または`MessageHeaders`インスタンス。 一部のオーバーロードはヘッダーを&1; つだけコピーします。すべてのヘッダーをコピーする別のオーバーロードもあります。 <xref:System.ServiceModel.Channels.MessageHeaders.Clear%2A>メソッドは、すべてのヘッダーを削除します。 <xref:System.ServiceModel.Channels.MessageHeaders.RemoveAt%2A>メソッドは、(その後にすべてのヘッダーをシフト) 特定のインデックス位置にあるヘッダーを削除します。 <xref:System.ServiceModel.Channels.MessageHeaders.RemoveAll%2A>メソッドは、特定の名前と名前空間のすべてのヘッダーを削除します。  
  
 特定のヘッダーを使用して、取得、 <xref:System.ServiceModel.Channels.MessageHeaders.FindHeader%2A>メソッドです。 このメソッドは、検索するヘッダーの名前と名前空間を受け取り、そのインデックスを返します。 複数のヘッダーが見つかった場合は、例外がスローされます。 ヘッダーが見つからなかい場合は、-1 が返されます。  
  
 SOAP ヘッダー モデルでは、ヘッダーに `Actor` 値を持たせ、ヘッダーの受信者を指定できます。 最も基本的な `FindHeader` オーバーロードでは、メッセージの最終受信者を表すヘッダーのみを検索します。 ただし、別のオーバーロードでは、検索に含める `Actor` 値を指定できます。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]、SOAP 仕様を参照してください。  
  
 A [CopyTo (MessageHeaderInfo\<xref:System.ServiceModel.Channels.MessageHeaders.CopyTo%28System.ServiceModel.Channels.MessageHeaderInfo%5B%5D%2CSystem.Int32%29>からヘッダーをコピーする方法が提供される、 <xref:System.ServiceModel.Channels.MessageHeaders>の配列にコレクション<xref:System.ServiceModel.Channels.MessageHeaderInfo>オブジェクトです。  
  
 ヘッダー内の XML データにアクセスするに呼び出すことができます<xref:System.ServiceModel.Channels.MessageHeaders.GetReaderAtHeader%2A>し、特定のヘッダー インデックスの XML リーダーを返します。 ヘッダーの内容をオブジェクトに逆シリアル化する場合は、使用<xref:System.ServiceModel.Channels.MessageHeaders.GetHeader%60%601%28System.Int32%29>または他のオーバー ロードのいずれかです。 最も基本的なオーバー ロードを使用してヘッダーを逆シリアル化、 <xref:System.Runtime.Serialization.DataContractSerializer>既定値で構成されている方法です。 異なるシリアライザーを使用したり、異なる構成の `DataContractSerializer` を使用したりする場合は、`XmlObjectSerializer` を受け取るオーバーロードの&1; つを使用します。 インデックスの代わりに、ヘッダー名、名前空間、オプションとして `Actor` 値のリストを受け取るオーバーロードもあります。これは、`FindHeader` と `GetHeader` の組み合わせです。  
  
## <a name="working-with-properties"></a>プロパティの操作  
 `Message` インスタンスには、任意の数の任意の型の名前付きオブジェクトを含めることができます。 このコレクションは、`Properties` 型の `MessageProperties` プロパティを使用してアクセスできます。 コレクションを実装、 <xref:System.Collections.Generic.IDictionary%602>インターフェイスし、のマッピングの役割を果たします<xref:System.String>に<xref:System.Object>\</TKey, TValue>。 通常、プロパティの値は、ネットワーク上のメッセージの一部に直接マップされないが、さまざまなメッセージ処理のヒントのさまざまなチャンネルを提供、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]チャネル スタックや、 [CopyTo (MessageHeaderInfo\<xref:System.ServiceModel.Channels.MessageHeaders.CopyTo%28System.ServiceModel.Channels.MessageHeaderInfo%5B%5D%2CSystem.Int32%29>サービス フレームワークです。 例については、次を参照してください。[データ転送のアーキテクチャ概要](../../../../docs/framework/wcf/feature-details/data-transfer-architectural-overview.md)します。  
  
## <a name="inheriting-from-the-message-class"></a>Message クラスからの継承  
 `CreateMessage` を使用して作成された組み込みのメッセージ型がユーザーの要件を満たさない場合は、`Message` クラスから派生するクラスを作成します。  
  
### <a name="defining-the-message-body-contents"></a>メッセージ本文の内容の定義  
 メッセージ本文内のデータにアクセスする主な手法は、書き込み、読み取り、バッファーへのコピーの&3; つです。 これらの操作は、最終的に、 <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%2A>、 <xref:System.ServiceModel.Channels.Message.OnGetReaderAtBodyContents%2A>、および<xref:System.ServiceModel.Channels.Message.OnCreateBufferedCopy%2A>メソッドの呼び出しに、それぞれの派生クラスで`Message`します。 `Message` 基本クラスでは、これらのメソッドは `Message` インスタンスごとに&1; つしか呼び出されないようになっており、そのメソッドが&2; 回以上呼び出されることもありません。 また、この基本クラスは、閉じられているメッセージでメソッドが呼び出されないことも保証します。 実装の中でメッセージ状態を追跡する必要はありません。  
  
 <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%2A>抽象メソッドで、実装する必要があります。 メッセージの本文内容を定義する最も基本的な方法は、このメソッドを使用して書き込むことです。 たとえば、次のメッセージには 1 から 20 までの 100,000 個の乱数が含まれています。  
  
 [!code-csharp[C_UsingTheMessageClass#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#9)]
 [!code-vb[C_UsingTheMessageClass#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#9)]  
  
 
          `OnGetReaderAtBodyContents` メソッドと `OnCreateBufferedCopy` メソッドには、ほとんどの場合に有効な既定の実装があります。 既定の実装は、`OnWriteBodyContents` を呼び出し、結果をバッファーに格納して、格納後のバッファーを操作します。 ただし、これが十分ではない場合もあります。 前の例では、メッセージを読み込むと 100,000 個の XML 要素がバッファーに格納されることになりますが、これは望ましくありません。 `OnGetReaderAtBodyContents` をオーバーライドすると、乱数を提供するカスタムの `XmlDictionaryReader` 派生クラスを返すことができます。 これで、`OnWriteBodyContents` をオーバーライドして、`OnGetReaderAtBodyContents` プロパティから返されたリーダーを使用できます。この例を次に示します。  
  
 [!code-csharp[C_UsingTheMessageClass#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#10)]
 [!code-vb[C_UsingTheMessageClass#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#10)]  
  
 同様に `OnCreateBufferedCopy` をオーバーライドして、独自の `MessageBuffer` 派生クラスを返すこともできます。  
  
 メッセージの派生クラスでは、メッセージ本文の内容を提供するだけでなく、`Version`、`Headers`、`Properties` の各プロパティをオーバーライドする必要もあります。  
  
 メッセージのコピーを作成した場合、作成したコピーでは、元のメッセージのメッセージ ヘッダーが使用されます。  
  
### <a name="other-members-that-can-be-overridden"></a>オーバーライド可能なその他のメンバー  
 オーバーライドすることができます、 <xref:System.ServiceModel.Channels.Message.OnWriteStartEnvelope%2A>、 <xref:System.ServiceModel.Channels.Message.OnWriteStartHeaders%2A>、および<xref:System.ServiceModel.Channels.Message.OnWriteStartBody%2A> SOAP エンベロープ、SOAP ヘッダーと SOAP 本文要素のタグを起動する方法を指定する方法が書き込まれます。 通常、これらは、`<soap:Envelope>`、`<soap:Header>`、および `<soap:Body>` に対応します。 一般的に、`Version` プロパティで `MessageVersion.None` が返された場合、これらのメソッドで何も書き込まないでください。  
  
> [!NOTE]
>  `OnGetReaderAtBodyContents` の既定の実装では、`OnWriteStartEnvelope` を呼び出して結果をバッファーに格納する前に、`OnWriteStartBody` と `OnWriteBodyContents` を呼び出します。 ヘッダーは書き込まれません。  
  
 オーバーライド、 <xref:System.ServiceModel.Channels.Message.OnWriteMessage%2A>メソッドで、さまざまな部分からメッセージ全体を構築する方法を変更します。 `OnWriteMessage`からメソッドを呼び出した<xref:System.ServiceModel.Channels.Message.WriteMessage%2A>や既定<xref:System.ServiceModel.Channels.Message.OnCreateBufferedCopy%2A>実装します。 オーバーライドすることに注意してください<xref:System.ServiceModel.Channels.Message.WriteMessage%2A>ベスト プラクティスではありません。 適切な上書きすることをお勧め`On`メソッド (たとえば、 <xref:System.ServiceModel.Channels.Message.OnWriteStartEnvelope%2A>、 <xref:System.ServiceModel.Channels.Message.OnWriteStartHeaders%2A>、および<xref:System.ServiceModel.Channels.BodyWriter.OnWriteBodyContents%2A>します。  
  
 オーバーライド<xref:System.ServiceModel.Channels.Message.OnBodyToString%2A>をデバッグ中のメッセージ本文の表現方法をオーバーライドします。 既定では、3 つのドット ("...") で表されます。 このメソッドは、メッセージの状態が Closed 以外のときに複数回呼び出すことができます。 このメソッドを実装すると、1 度だけ実行する必要のある処理 (転送のみのストリームからの読み取りなど) は発生しません。  
  
 オーバーライド、 <xref:System.ServiceModel.Channels.Message.OnGetBodyAttribute%2A>メソッド、SOAP 本文要素の属性へのアクセスを許可するようにします。 このメソッドは何度でも呼び出すことができますが、`Message` 基本型は、メッセージの状態が Created の時にのみ呼び出されることを保証します。 実装の中で状態をチェックする必要はありません。 既定の実装は、本文要素に属性がないことを示す `null` を常に返します。  
  
 場合、`Message`オブジェクトでは、メッセージ本文が必要でなくなったときに特別なクリーンアップを実行する必要があります、オーバーライドする<xref:System.ServiceModel.Channels.Message.OnClose%2A>します。 既定の実装では、何も行われません。  
  
 `IsEmpty` プロパティと `IsFault` プロパティは、オーバーライド可能です。 既定では、両方とも `false` を返します。