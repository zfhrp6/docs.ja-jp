---
title: "WebRequest からの派生 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "WebRequest クラス、プラグ可能なプロトコル"
  - "プロトコル固有の要求ハンドラー"
  - "送信 (データを)、プラグ可能なプロトコル"
  - "プラグ可能なプロトコル、クラスの基準"
  - "インターネット、プラグ可能なプロトコル"
  - "受信 (データを)、プラグ可能なプロトコル"
  - "プロトコル、プラグ可能"
ms.assetid: 9810c177-973e-43d7-823c-14960bd625ea
caps.latest.revision: 9
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 7
---
# WebRequest からの派生
<xref:System.Net.WebRequest> クラスは、.NET Framework プラグインの可能なプロトコル モデルに対応するプロトコル ハンドラーの要求を作成する基本およびメソッド プロパティを提供する抽象的な基本クラスです。  **\[WebRequest\]** クラスを使用するアプリケーションは、サポートされるプロトコルを使用して使用されるプロトコルを指定する必要なく、データを要求できます。  
  
 2 種類の基準はプラグイン可能なプロトコルとして使用するプロトコル対応クラスに対して満たす必要があります: クラスは、<xref:System.Net.IWebRequestCreate> インターフェイスを実装し <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=fullName> 方法と登録する必要があります。  クラスはプラグイン可能なインターフェイスを提供する **\[WebRequest\]** のすべての抽象的な方法およびプロパティを必要があります。  
  
 **\[WebRequest\]** のインスタンスは一度だけの使用を意図しています; 別の要求をする場合は、新しい **\[WebRequest\]**を作成します。  **\[WebRequest\]** は、テンプレート **\[WebRequest\]** を XML し、追加要求のテンプレートを再構築する開発者のを有効にするに <xref:System.Runtime.Serialization.ISerializable> インターフェイスをサポートします。  
  
## IWebRequest が方法を作成します  
 <xref:System.Net.IWebRequestCreate.Create%2A> 方法はプロトコル対応クラスの新しいインスタンスを初期化する責任があります。  新しい **\[WebRequest\]** が作成されると、<xref:System.Net.WebRequest.Create%2A?displayProperty=fullName> 方法は **RegisterPrefix** 方法と登録された URI の接頭辞に要求された URI を照合します。  適切な対応プロトコルその子孫の **\[作成\]** 方法に変更されるプロトコル対応するフィールドは必要ではありませんプロトコルの標準的な要求または応答のトランザクションを実行できる子孫の初期化したインスタンスを戻す必要があります。  
  
## ConnectionGroupName のプロパティ  
 複数の要求を単一の接続を作成できるように <xref:System.Net.WebRequest.ConnectionGroupName%2A> のプロパティがリソース グループへの接続を表示するために使用します。  接続共有を実行するには、割り当てる接続プール プロトコル対応方法を使用します。  たとえば、<xref:System.Net.HttpWebRequest> クラスで共有する出荷済 <xref:System.Net.ServicePointManager> クラスの実装のつながり。  各接続のグループを特定のサーバーへの接続を提供する **ServicePointManager** のクラスが <xref:System.Net.ServicePoint> を作成します。  
  
## ContentLength のプロパティ  
 <xref:System.Net.WebRequest.ContentLength%2A> のプロパティはデータをアップロードするとサーバーに送信されるデータのバイト数を指定します。  
  
 通常、アップロードが **\[ContentLength\]** のプロパティがゼロより大きい値に設定されている場合行われていることを示すには <xref:System.Net.WebRequest.Method%2A> のプロパティが設定されている必要があります。  
  
## ContentType のプロパティ  
 <xref:System.Net.WebRequest.ContentType%2A> のプロパティは、送信されるコンテンツ タイプを識別するために、プロトコルとサーバーに送信するように要求すると特殊な情報を提供します。  通常、これはアップロードされるすべてのデータの MIME のコンテンツ タイプです。  
  
## 資格情報のプロパティ  
 <xref:System.Net.WebRequest.Credentials%2A> のプロパティは、サーバーと要求を認証するための情報が含まれます。  自分のプロトコルと認証プロセスの詳細を行う必要があります。  <xref:System.Net.AuthenticationManager> のクラスが要求を認証および認証トークンを提供する責任があります。  自分のプロトコルで使用される資格情報を提供するクラスが <xref:System.Net.ICredentials> インターフェイスを行う必要があります。  
  
## ヘッダーのプロパティ  
 <xref:System.Net.WebRequest.Headers%2A> のプロパティは要求に関連付けられたメタデータの名前と値の組み合わせのコレクション オプションが含まれます。  名前と値の組み合わせで表すことができるプロトコルが必要とするしたメタデータが **\[ヘッダー\]** のプロパティに含めることができます。  通常この情報は <xref:System.Net.WebRequest.GetRequestStream%2A> または <xref:System.Net.WebRequest.GetResponse%2A> 方法を追加する前に設定する必要があります; 一度要求は、メタデータ、見なされます読み取り専用に作成されます。  
  
 ヘッダーのメタデータを使用するに **\[ヘッダー\]** のプロパティを使用する必要はありません。  プロトコル対応のメタデータをプロパティとして公開できます。; たとえば、<xref:System.Net.HttpWebRequest.UserAgent%2A?displayProperty=fullName> のプロパティは **User\-Agent** の HTTP ヘッダーを公開します。  プロパティとしてヘッダーのメタデータを公開すると、同じプロパティが **\[ヘッダー\]** のプロパティを使用するように設定できません。  
  
## 方法のプロパティ  
 <xref:System.Net.WebRequest.Method%2A> のプロパティは要求がサーバーに実行するように依頼するか動詞アクションが含まれます。  **\[メソッド\]** プロパティの既定値はプロトコル対応するプロパティがある必要はありませんの標準的な要求または応答のアクションを有効にする必要があります。  たとえば、Web サーバーからリソースを要求し、応答を返品 [HttpWebResponse](frlrfSystemNetHttpWebResponseClassMethodTopic) 方法は得るためになります。  
  
 通常ある場合 **\[ContentLength\]** の **\[メソッド\]** のプロパティがアップロードが行われていることを示します動詞アクションまたはに設定されている場合プロパティが大きい値に設定する必要があります。  
  
## PreAuthenticate のプロパティ  
 アプリケーションは認証情報が必要であることを示すに <xref:System.Net.WebRequest.PreAuthenticate%2A> のプロパティを設定チャレンジを待機しています。認証ではなく、初期需要ととも。  **\[前もって認証\]** のプロパティはプロトコルが最初の要求に送信される資格情報を認証をサポート場合にのみ意味を使用しています。  
  
## プロキシのプロパティ  
 <xref:System.Net.WebRequest.Proxy%2A> のプロパティは、要求されたリソースのアクセスに使用される <xref:System.Net.IWebProxy> インターフェイスが含まれます。  **\[プロキシ\]** のプロパティは、プロトコルが proxied 要求をサポートする場合にのみ意味を使用しています。  1 種類が、プロトコルによって要求される既定のプロキシを設定する必要があります。  
  
 会社のファイアウォールの後などのある環境では、プロキシを使用するには、プロトコルが必要な場合があります。  この場合、プロトコルで働くプロキシ クラスを作成するに **IWebProxy** インターフェイスを行う必要があります。  
  
## RequestUri のプロパティ  
 <xref:System.Net.WebRequest.RequestUri%2A> のプロパティは **\[WebRequest.Create\]** 方法に渡した URI が含まれます。  これは **\[WebRequest\]** が作成されている場合は読み取り専用で、変更することはできません。  自分のプロトコルがリダイレクトをサポートしている場合、応答を別の URI によって識別されるリソースから取得できます。  応募した URI へのアクセスを許可する必要がある場合は、その URI を含む追加のプロパティを指定する必要があります。  
  
## タイムアウトのプロパティ  
 <xref:System.Net.WebRequest.Timeout%2A> のプロパティは、時間 \(ミリ秒単位で、要求の前に待機時間を時間を日時投げます例外が含まれます。  **\[タイムアウト\]** は <xref:System.Net.WebRequest.GetResponse%2A> 方法との同期要求に対してのみです; 非同期要求が保留中で要求を取り消すために <xref:System.Net.WebRequest.Abort%2A> 方法を使用する必要があります。  
  
 **\[タイムアウト\]** のプロパティの設定はプロトコル対応クラスのタイムアウト プロセスを実行する場合にのみ意味を使用しています。  
  
## 中止方法  
 <xref:System.Net.WebRequest.Abort%2A> 方法は、サーバーは保留中の非同期要求を取り消します。  要求が取り消された後、**GetResponse**を、**BeginGetResponse**すると、**EndGetResponse**、**GetRequestStream**、**BeginGetRequestStream**、または **EndGetRequestStream** は [RequestCanceled](frlrfSystemNetWebExceptionStatusClassTopic)に <xref:System.Net.WebException.Status%2A> のプロパティとの <xref:System.Net.WebException> を投げます。  
  
## BeginGetRequestStream と EndGetRequestStream 方法  
 <xref:System.Net.WebRequest.BeginGetRequestStream%2A> 方法は、サーバーにデータをアップロードするために使用されるストリームの非同期要求を開始します。  <xref:System.Net.WebRequest.EndGetRequestStream%2A> 方法は非同期要求を完了して、要求されたストリームを返します。  これらの方法には標準 .NET Framework 非同期のパターンを使用して **GetRequestStream** 方法を実行します。  
  
## BeginGetResponse と EndGetResponse 方法  
 <xref:System.Net.WebRequest.BeginGetResponse%2A> 方法は非同期サーバーに要求を開始します。  <xref:System.Net.WebRequest.EndGetResponse%2A> 方法は非同期要求を完了して、要求された応答を返します。  これらの方法には標準 .NET Framework 非同期のパターンを使用して **GetResponse** 方法を実行します。  
  
## GetRequestStream 方法  
 <xref:System.Net.WebRequest.GetRequestStream%2A> 方法は、要求されたサーバーにデータを入力するために使用されるストリームを返します。  返品ストリームは検索する書き込み専用ストリーム必要です; これは、サーバーに書き込まれる一方の通行データのベースとして使用されます。  ストリームは <xref:System.IO.Stream.CanRead%2A> と <xref:System.IO.Stream.CanSeek%2A> のプロパティの false を返品した <xref:System.IO.Stream.CanWrite%2A> のプロパティに調整します。  
  
 **GetRequestStream** 方法はストリームを行う前に、データがサーバーに送信することをサーバーへの接続を開き、ヘッダー情報を表示します。  **GetRequestStream** が要求を開始するので、**ヘッダー** プロパテや **\[ContentLength\]** のプロパティの設定は **GetRequestStream**を追加した後、通常は許可されません。  
  
## GetResponse 方法  
 <xref:System.Net.WebRequest.GetResponse%2A> 方法がサーバーからの応答を表す <xref:System.Net.WebResponse> クラス プロトコル対応その子孫を返します。  要求が **GetRequestStream** 方法で既に始められなかったら、**GetResponse** 方法は **RequestUri**に応じて、請求要求のタイプを示す送信ヘッダー情報への接続を作成して識別されるリソース、リソースからの応答が表示されます。  
  
 **GetResponse** 方法が呼び出されなかった場合、すべてのプロパティは読み取り専用に考慮する必要があります。  **\[WebRequest\]** のインスタンスは一度だけの使用を意図しています; 別の要求をする場合は、新しい **\[WebRequest\]**を作成する必要があります。  
  
 **GetResponse** 方法は、受信する応答を含めるに **WebResponse** の適切な子孫を作成する担当者があります。  
  
## 参照  
 <xref:System.Net.WebRequest>   
 <xref:System.Net.HttpWebRequest>   
 <xref:System.Net.FileWebRequest>   
 [プラグ可能なプロトコルのプログラミング](../../../docs/framework/network-programming/programming-pluggable-protocols.md)   
 [WebResponse からの派生](../../../docs/framework/network-programming/deriving-from-webresponse.md)