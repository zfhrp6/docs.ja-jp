---
title: "統合 Windows 認証と拡張保護 | Microsoft Docs"
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
ms.assetid: 81731998-d5e7-49e4-ad38-c8e6d01689d0
caps.latest.revision: 13
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 13
---
# 統合 Windows 認証と拡張保護
改良は、統合 Windows 認証が <xref:System.Net> の <xref:System.Net.HttpWebRequest>によって、<xref:System.Net.HttpListener>、<xref:System.Net.Mail.SmtpClient>、<xref:System.Net.Security.SslStream>、および関連 <xref:System.Net.Security.NegotiateStream>クラスおよび関連名前空間の処理にその影響に作成されました。  拡張サポートされていますがセキュリティ保護を高めることができるように追加されました。  
  
 これらの変更は、Web を要求し、統合 Windows 認証が使用される応答を受け取るには、これらのクラスを使用するアプリケーションに影響を与える可能性があります。  この変更は、統合 Windows 認証を使用するようにコンフィギュレーションされているクライアント アプリケーションと Web サーバーに影響を与える可能性があります。  
  
 これらの変更は他のタイプの要求を選択し、統合 Windows 認証が使用される応答を受け取るには、これらのクラスを使用するアプリケーションに影響を与える可能性があります。  
  
 拡張サポートするためにの変更は、Windows 7 および Windows Server 2008 R2 のアプリケーション用にのみ使用できます。  拡張保護機能は、以前のバージョンの Windows で使用できません。  
  
## 概要  
 統合 Windows 認証は、資格情報のチャレンジ応答が汎用的で、再利用または転送できるように設計されています。  課題応答では、少なくともチャンネルに固有の情報ターゲットの特定の情報と組み立てできる必要があります。  サービスは、クレデンシャルの課題応答をサービスプリンシパル \(SPN\) 名など、サービス別の情報を含んでいることを確認する拡張保護を提供できます。  クレデンシャル交換にこの情報を使用して、サービスは Administrators に使用できるクレデンシャルの課題の応答悪意のある使用への対策を上書きできます。  
  
 拡張保護のデザインが認証リレー攻撃を軽減するように設計されている認証に改良プロトコルです。  これは、チャンネルおよびサービスのバインディング情報の概念に関して有効にします。  
  
 全体的な目的は次があります:  
  
1.  拡張保護をサポートするためのクライアント アプリケーションを更新する場合は、すべてのサポートされて認証プロトコルのチャンネルにバインドおよびサービスのバインディング情報を供給する必要があります。  チャンネルの情報はバインディングにバインドされるチャンネル \(TLS\) がある場合にのみ提供できます。  サービスのバインディング情報は常に指定する必要があります。  
  
2.  適切にコンフィギュレーションされている更新されたサーバーは、チャンネルののにが一致しない場合は、クライアント認証のトークンに確認し、認証の送信をことがあるかも知れませんチャンネルおよびサービスのバインディング情報を却下します。  配置のシナリオで、サーバーは、チャンネルののに、サービスのにまたは両方を確認することがあります。  
  
3.  更新されたサーバーにポリシーに基づいたチャンネルのバインディング情報を含まないレベルのクライアント要求を承認または否認することもできます。  
  
 拡張保護で使用される情報は、次の 2 人の一部の 1 人または両方から構成されています:  
  
1.  チャンネルの結合のトークンまたは CBT。  
  
2.  サービスプリンシパル名または SPN の形式のサービス バインディング情報。  
  
 サービスのバインディング情報は、そのサービス エンドポイントに認証するクライアントの目的を示しますです。  これは次のプロパティとクライアントからサーバーへの伝えられます:  
  
-   SPN の値はクリア テキストの認証フォームでクライアントを実行しているサーバーに使用可能である必要があります。  
  
-   SPN の値は、パブリックです。  
  
-   SPN は男性中間の攻撃の値を挿入、削除、または変更できません。インターネットに輸送中に対して作成された保護する必要があります。  
  
 CBT は、内部の認証したチャンネル、クライアント上の通話内容に \(バインド\) それを結ぶに使用される外部の保護されたチャネルのプロパティ \(TLS など\) です。  CBT は、次のプロパティがあります \(または IETF の RFC 5056 で指定\) 場合:  
  
-   外部のチャンネルである場合、CBT の値は外部のチャンネルまたは個別に通話内容のクライアントではなく、およびサーバー側の到着サーバーのエンドポイント、識別するプロパティである必要があります。  
  
-   クライアントが送信 CBT の値は攻撃者が影響する物である必要があります。  
  
-   保証には、CBT の値の秘密について行われません。  ただし、CBT を伝えるプロトコルとしてのサービスのに、チャンネルのバインディング情報の値がそのほかの認証を実行するサーバーでも常に行われることができます。は暗号化する場合があります意味します。  
  
-   CBT は攻撃者が値を挿入、削除、または変更できません。輸送中に対して作成された保護されたインターネットに整合性である必要があります。  
  
 チャンネルののには tamperproof 方法に SPN サーバーと CBT を移動したクライアントによって行われます。  サーバーは、ポリシーに従ってチャンネルのバインディング情報を検証して、それ自身が意図されている目標にすると信じない認証の送信を却下します。  この方法では、2 種類の暗号チャンネルに組み合わせてバインドされたようになります。  
  
 既存のクライアントのアプリケーションと互換性を管理するには、サーバーは、拡張保護をサポートするいないクライアントによって認証の送信を許可するようにコンフィギュレーションされている場合があります。  これは、「完全に確かされた」コンフィギュレーションとは異なります。「部分的に確かしたコンフィギュレーション」、と呼ばれます。  
  
 <xref:System.Net> の複数のコンポーネントと <xref:System.Net.Security> の名前空間の名前はアプリケーションに代わって統合 Windows 認証を実行します。  このセクションでは、統合 Windows 認証内の拡張保護を追加するに System.Net のコンポーネントに対する変更について説明します。  
  
 拡張保護は、Windows 7 で現在サポートされます。  メカニズムは提供されるので、アプリケーションは、オペレーティング システムが拡張保護をサポートするかどうかを決定できます。  
  
## 拡張サポートするためにの変更  
 使用される認証プロトコルで統合 Windows 認証で使用される認証プロセスは、多くの場合、設定先のコンピュータで発行、クライアント コンピュータにレシート実行する課題が含まれます。  拡張保護は、この承認プロセスに新しい機能を追加  
  
 <xref:System.Security.Authentication.ExtendedProtection> 名前空間は、アプリケーションの拡張保護を使用した認証をサポートします。  この名前空間の <xref:System.Security.Authentication.ExtendedProtection.ChannelBinding> クラスは、チャンネルののにを表します。  この名前空間の <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> クラスは、受信するクライアント接続の検証にサーバーが使用する拡張保護するポリシーを表します。  他のクラスのメンバは、拡張ために使用されます。  
  
 サーバー アプリケーションの場合は、これらのクラスが含まれています:  
  
 <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> 次の要素があります:  
  
-   オペレーティング システムには拡張保護する連結ウィンドウの認証をサポートするかどうかを示す <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.OSSupportsExtendedProtection%2A> のプロパティ。  
  
-   拡張保護ポリシーを適用するタイミングを示す <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> 値。  
  
-   配置のシナリオを示す <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario> の値。  拡張保護を確認できますが、その影響します。  
  
-   オプション <xref:System.Security.Authentication.ExtendedProtection.ServiceNameCollection> はクライアントによって注文の SPN の一覧が表示されます SPN と照合するために使用する際に認証を置くターゲット提供します。  
  
-   オプション <xref:System.Security.Authentication.ExtendedProtection.ChannelBinding> 検証に使用する注文のチャンネルののにがあります。  このシナリオでは、一般的なケースではありません  
  
 <xref:System.Security.Authentication.ExtendedProtection.Configuration> 名前空間は、アプリケーションの拡張保護を使用した認証の構成をサポートします。  
  
 いくつかの機能の変更は <xref:System.Net> の既存の名前空間の拡張保護をサポートするために対しています。  これらの変更は、次が含まれています:  
  
-   <xref:System.Net.TransportContext> の新しいクラス、転送のコンテキストを表す <xref:System.Net> の名前空間に追加される日数。  
  
-   <xref:System.Net.HttpWebRequest> の新しい <xref:System.Net.HttpWebRequest.EndGetRequestStream%2A> およびクライアント アプリケーションの拡張保護をサポートするために <xref:System.Net.TransportContext> の取得を割り当てる <xref:System.Net.HttpWebRequest.GetRequestStream%2A> 過負荷の方法が分類されます。  
  
-   サーバー アプリケーションをサポートする <xref:System.Net.HttpListener> と <xref:System.Net.HttpListenerRequest> クラスに関連付けます。  
  
 機能の変更は <xref:System.Net.Mail> の既存の名前空間の SMTP のクライアント アプリケーションの拡張保護をサポートするされています。:  
  
-   拡張ときに保護を SMTP のクライアント アプリケーションで使用する認証に使用する SPN を表す <xref:System.Net.Mail.SmtpClient> クラスの <xref:System.Net.Mail.SmtpClient.TargetName%2A> のプロパティ。  
  
 いくつかの機能の変更は <xref:System.Net.Security> の既存の名前空間の拡張保護をサポートするために対しています。  これらの変更は、次が含まれています:  
  
-   <xref:System.Net.Security.NegotiateStream> の新しい <xref:System.Net.Security.NegotiateStream.BeginAuthenticateAsClient%2A> およびクライアント アプリケーションのサポートの拡張保護に CBT を渡すことを割り当てる <xref:System.Net.Security.NegotiateStream.AuthenticateAsClient%2A> 過負荷の方法が分類されます。  
  
-   <xref:System.Net.Security.NegotiateStream> の新しい <xref:System.Net.Security.NegotiateStream.BeginAuthenticateAsServer%2A> サーバーおよびアプリケーションのサポートの拡張保護に <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> を渡すことを割り当てる <xref:System.Net.Security.NegotiateStream.AuthenticateAsServer%2A> 過負荷の方法が分類されます。  
  
-   クライアントとサーバー アプリケーションの拡張保護をサポートする <xref:System.Net.Security.SslStream> クラスの <xref:System.Net.Security.SslStream.TransportContext%2A> の新しいプロパティ。  
  
 <xref:System.Net.Configuration.SmtpNetworkElement> のプロパティは <xref:System.Net.Security> の名前空間の SMTP のクライアントの拡張保護する場合のコンフィギュレーションに追加されました。  
  
## クライアント アプリケーションの拡張保護  
 ほとんどのクライアント アプリケーションの拡張やサポートは自動的に行われます。  <xref:System.Net.HttpWebRequest> と <xref:System.Net.Mail.SmtpClient> クラスは、Windows の基になるバージョンが拡張保護をサポートするたびに、拡張保護をサポートします。  <xref:System.Net.HttpWebRequest> のインスタンスは <xref:System.Uri>から組み立て SPN を送信します。  既定では、<xref:System.Net.Mail.SmtpClient> のインスタンスが SMTP メール サーバーのホスト名から組み立て SPN を送信します。  
  
 注文の認証に、クライアント アプリケーションは <xref:System.Net.HttpWebRequest.EndGetRequestStream%28System.IAsyncResult%2CSystem.Net.TransportContext%40%29?displayProperty=fullName> を使用することも、<xref:System.Net.TransportContext.GetChannelBinding%2A> 方法を使用して <xref:System.Net.TransportContext> と CBT の取得を割り当てる <xref:System.Net.HttpWebRequest> の <xref:System.Net.HttpWebRequest.GetRequestStream%28System.Net.TransportContext%40%29?displayProperty=fullName> 方法が分類されます。  
  
 特定のサービスに <xref:System.Net.HttpWebRequest> のインスタンスに送信統合 Windows 認証に使用する SPN は <xref:System.Net.AuthenticationManager.CustomTargetNameDictionary%2A> のプロパティの設定によって上書きできます。  
  
 Windows 統合認証に使用する SMTP の接続の場合は <xref:System.Net.Mail.SmtpClient.TargetName%2A> のプロパティが注文の SPN を設定するために使用できます。  
  
## サーバー アプリケーションの拡張保護  
 <xref:System.Net.HttpListener> は、サービスののにを検証するに自動的に HTTP 認証を実行するとメカニズムを提供します。  
  
 最も安全なシナリオは HTTPS:\/\/ の接頭辞の拡張保護を有効にすることです。  この場合、<xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> の <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> に <xref:System.Net.HttpListener.ExtendedProtectionPolicy%2A?displayProperty=fullName> を設定します <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> または <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement>にし、<xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> の <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario> A の値に設定 <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario> を部分的に確かした荷渡方法に <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> が完全に確かした荷渡方法に対応しますが、<xref:System.Net.HttpListener> を設定します。  
  
 このコンフィギュレーションでは要求が外部の保護されたチャネルによるサーバーに行われると、外部のチャンネルは、チャンネルののににただされます。  このチャンネルの検証するのには、認証 SSPI の呼び出しに認証 BLOB のチャンネルののにを照合するに渡されます。  3 可能な結果があります:  
  
1.  サーバーの基になるオペレーティング システムには拡張保護はサポートされません。  要求はアプリケーションに公開されておらず、無許可 \(401\) 回答はクライアントになります。  メッセージが失敗の理由を指定する <xref:System.Net.HttpListener> の追跡ソースに記録されます。  
  
2.  SSPI の電話のいずれかがクライアント サーバーの拡張保護するポリシーが <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement>用にコンフィギュレーションされたときに該当しなくなり外部のチャンネルまたはクライアントから取得した予測値にバインドのチャンネルを指定されていないのにのチャンネルを指定します。失敗したことを示します。  どちらの場合も、要求はアプリケーションに公開されておらず、無許可 \(401\) 回答はクライアントになります。  メッセージが失敗の理由を指定する <xref:System.Net.HttpListener> の追跡ソースに記録されます。  
  
3.  クライアントとサーバーの拡張保護するポリシーが要求が処理のアプリケーションに戻ります <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> にコンフィギュレーションされているため、正しいチャンネルののにを指定したり、チャンネルののにを指定せずに接続するに割り当てられます。  サービス名の小切手が自動的に実行されません。  <xref:System.Net.HttpListenerRequest.ServiceName%2A> のプロパティを使用して独自のサービス名の検証を実行するこのような状況で追加です。  
  
 HTTP 要求の本文テキスト内で前後の出荷 BLOB に基づいて認証を実行するには、アプリケーションが独自の SSPI の通話を行い、チャンネルののにをサポートたければネイティブ Win32 [AcceptSecurityContext](http://go.microsoft.com/fwlink/?LinkId=147021) 機能に渡すために <xref:System.Net.HttpListener> を使用して外部の保護されたチャネルから予期したチャンネルののにを取得する必要があります。  これを行うには、<xref:System.Net.HttpListenerRequest.TransportContext%2A> のプロパティを使用し、CBT を取得するに <xref:System.Net.TransportContext.GetChannelBinding%2A> 方法を追加します。  エンドポイントののにのみがサポートされます。  何も指定されている場合、他の <xref:System.Security.Authentication.ExtendedProtection.ChannelBindingKind><xref:System.NotSupportedException> は投げられます。  基になるオペレーティング システムのサポートをのにを運べば、<xref:System.Net.TransportContext.GetChannelBinding%2A> 方法は `pInput` パラメータで渡した SecBuffer 構造の pvBuffer のメンバとして機能に [AcceptSecurityContext](http://go.microsoft.com/fwlink/?LinkId=147021) 渡されることに適したチャンネルののににポインタをラップする <xref:System.Security.Authentication.ExtendedProtection.ChannelBinding><xref:System.Runtime.InteropServices.SafeHandle> を返します。  <xref:System.Security.Authentication.ExtendedProtection.ChannelBinding.Size%2A> のプロパティは、チャンネルののにのバイトで、長さが含まれます。  基になるオペレーティング システムのチャンネルをサポートのに、機能を `null`を返します。  
  
 別の可能なシナリオがプロキシを使用しない場合は、HTTP:\/\/ から接頭辞の拡張保護を有効にすることです。  この場合、<xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> の <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> に <xref:System.Net.HttpListener.ExtendedProtectionPolicy%2A?displayProperty=fullName> を設定します <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> または <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement>にし、<xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> の <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario> A の値に設定 <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario> を部分的に確かした荷渡方法に <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> が完全に確かした荷渡方法に対応しますが、<xref:System.Net.HttpListener> を設定します。  
  
 許可されるサービス名の既定の一覧は、<xref:System.Net.HttpListener>とともに登録されている接頭辞に基づいて作成されます。  この既定の一覧は、<xref:System.Net.HttpListener.DefaultServiceNames%2A> のプロパティを使用して行われることができます。  このリストを包括的な場合、アプリケーションは既定のサービス名の一覧の代わりに使用される <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> クラスに対してコンストラクターでカスタム サービス名のコレクションを指定できます。  
  
 このコンフィギュレーションで、要求がチャンネルののにの確認なしで保護されたチャネルの外部の認証の利益なしでサーバーに一般に。  認証が成功すると、コンテキストは、クライアントが許容されるサービス名の一覧に対して提供し、検証するサービス名にただされます。  4 可能な結果があります:  
  
1.  サーバーの基になるオペレーティング システムには拡張保護はサポートされません。  要求はアプリケーションに公開されておらず、無許可 \(401\) 回答はクライアントになります。  メッセージが失敗の理由を指定する <xref:System.Net.HttpListener> の追跡ソースに記録されます。  
  
2.  クライアントの基になるオペレーティング システムには拡張保護はサポートされません。  <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> のコンフィギュレーションの認証については、成功し、要求はアプリケーションになります。  <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> のコンフィギュレーションの認証については失敗します。  要求はアプリケーションに公開されておらず、無許可 \(401\) 回答はクライアントになります。  メッセージが失敗の理由を指定する <xref:System.Net.HttpListener> の追跡ソースに記録されます。  
  
3.  クライアントの基になるオペレーティング システムには拡張保護をサポートしていますが、アプリケーションは、サービスののにを指定していません。  要求はアプリケーションに公開されておらず、無許可 \(401\) 回答はクライアントになります。  メッセージが失敗の理由を指定する <xref:System.Net.HttpListener> の追跡ソースに記録されます。  
  
4.  クライアントがのサービスのにを指定します。  サービスののには許可されたサービスのにの一覧と比較されます。  これが一致した場合は、要求はアプリケーションになります。  それ以外の場合、要求はアプリケーションに公開されておらず、無許可 \(401\) 回答はクライアントに自動的に戻されます。  メッセージが失敗の理由を指定する <xref:System.Net.HttpListener> の追跡ソースに記録されます。  
  
 許容されるサービス名で許可されるリストを使用してこの単純な方法が不十分である場合、アプリケーションは <xref:System.Net.HttpListenerRequest.ServiceName%2A> のプロパティの問い合わせによって独自のサービス名の検証を提供できます。  ケース 1 と 2 では、上記に、プロパティは `null`を返します。  3 種類のフィールドが空白文字列を返す場合。  4 を、クライアントで指定したサービス名を返す場合。  
  
 これらの拡張保護機能は、要求の他の型と認証のサーバー アプリケーションによって信頼されたプロキシを使用する場合に使用します。  
  
## 参照  
 <xref:System.Security.Authentication.ExtendedProtection>   
 <xref:System.Security.Authentication.ExtendedProtection.Configuration>