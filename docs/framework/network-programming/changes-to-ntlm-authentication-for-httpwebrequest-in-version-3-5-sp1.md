---
title: "バージョン 3.5 SP1 における HttpWebRequest の NTLM 認証への変更 | Microsoft Docs"
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
ms.assetid: 8bf0b428-5a21-4299-8d6e-bf8251fd978a
caps.latest.revision: 8
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 8
---
# バージョン 3.5 SP1 における HttpWebRequest の NTLM 認証への変更
.NET Framework Version の 3.5 SP1、後でその影響のセキュリティの変更は、統合 Windows 認証が System.Net の名前空間の <xref:System.Net.HttpWebRequest>、<xref:System.Net.HttpListener>、および関連 <xref:System.Net.Security.NegotiateStream>クラス内をどのように処理されるか。されています。  これらの変更は、Web を要求し、NTLM に基づく統合 Windows 認証が使用される応答を受け取るには、これらのクラスを使用するアプリケーションに影響を与える可能性があります。  この変更は、統合 Windows 認証を使用するようにコンフィギュレーションされているクライアント アプリケーションと Web サーバーに影響を与える可能性があります。  
  
## 概要  
 Windows 統合認証のデザインを使用して、します。クレデンシャルの回答を普遍的にするには、には再利用したりできるようになります。  この特定のデザイン制限は、認証が必要であるプロトコル、ターゲットの特定の情報を伴う、特定の情報をまかなう必要です。  サービスは、クレデンシャルの回答をサービスプリンシパル \(SPN\) 名など、サービス別の情報を含んでいることを確認する拡張保護を提供できます。  クレデンシャル交換にこの情報を使用して、サービスは Administrators に計上する可能性があるクレデンシャルの応答悪意のある使用への対策を上書きできます。  
  
 <xref:System.Net> の複数のコンポーネントと <xref:System.Net.Security> の名前空間の名前はアプリケーションに代わって統合 Windows 認証を実行します。  このセクションでは、統合 Windows 認証内の拡張保護を追加するに System.Net のコンポーネントに対する変更について説明します。  
  
## 変更  
 Windows 統合認証に使用する NTLM 認証プロセスは先のコンピュータ設定して問題、クライアント コンピュータにレシート実行する課題が含まれます。  コンピュータがそれ自身を生成した課題を受け取る場合、認証が接続がループバックの接続 \(IPv4 の住所 127.0.0.1 など\) である失敗します。  
  
 内部 Web サーバーで実行中のサービスにアクセスと http:\/\/contoso\/service または https:\/\/contoso\/service と同様に、URL を使用してサービスにアクセスするために、共通です。  名前「」contoso は、多くの場合、サービスの展開 \(コンピュータのコンピュータ名ではありません。  Active Directory、DNS、NetBIOS を使用して <xref:System.Net> および関連する名前空間の場合、ローカル コンピュータのホスト \(通常は WWINDOWS\\system32\\drivers\\etc\\hosts など\) ファイルの名前、住所にを決済する場合は、またはローカル コンピュータの lmhosts \(通常 WINDOWS\\system32\\drivers\\etc\\lmhosts など\) ファイルします。  「」contoso に送信する要求が適切なサーバー コンピューターに送信して名前「」contoso が決済されます。  
  
 大規模な配置用にコンフィギュレーションされたときに、そのは、クライアント アプリケーションおよびエンド ユーザーが使用する的なコンピュータの名前で設定するにつれ、単一の仮想サーバーの名前に、共通ではありません。  たとえば、「」contoso のサーバーと内部ネットワークの単に電話 www.contoso.com する場合があります。  この名前は、クライアントのヘルプのホスト要求のヘッダーと呼ばれます。  HTTP プロトコルで指定されるように、ホスト ヘッダーのフィールドは必要なリソースのインターネット ホストとポート番号を指定します。  この情報は、ユーザーが提供またはリソース \(一般に、HTTP URL\) を参照する元の URI から取得されます。  .NET Framework Version 4 で、この情報には、<xref:System.Net.HttpWebRequest.Host%2A> の新しいプロパティを使用するクライアントに設定できます。  
  
 <xref:System.Net.AuthenticationManager> のクラスが <xref:System.Net.WebRequest> の派生クラスおよび的な <xref:System.Net.WebClient> クラスで使用される管理の認証のコンポーネント \(「」\) モジュールを制御します。  <xref:System.Net.AuthenticationManager> のクラスが <xref:System.Net.AuthenticationManager.CustomTargetNameDictionary%2A?displayProperty=fullName> のオブジェクトを公開する URI の文字列によって作成されるプロパティされたアプリケーションを認証時に使用される注文の SPN の文字列を提供する提供します。  
  
 Version 3.5 SP1 の既定では、<xref:System.Net.AuthenticationManager.CustomTargetNameDictionary%2A> プロパティが設定されていない場合、要求 URL で使用されているホスト名が NTLM \(NT LAN Manager\) 認証交換の SPN に指定されます。  要求 URL で使用されているホスト名は、クライアント要求の <xref:System.Net.HttpRequestHeader?displayProperty=fullName> に指定されている Host ヘッダーと異なる場合があります。  要求 URL で使用されているホスト名は、サーバーの実際のホスト名、サーバーのコンピューター名、コンピューターの IP アドレス、またはループバック アドレスと異なる場合があります。  このような場合は、Windows で認証要求が失敗します。  問題を処理するために、クライアント要求 \(「」contoso 使用されるホスト名がなど\) の URL で実際にローカル コンピュータの Windows 代替名であることを通知する必要があります。  
  
 この変更を行うに関してサーバー アプリケーションのいくつかの可能な方法があります。  推奨される方法は、サーバーの `BackConnectionHostNames` レジストリ キーに要求の URL で使用されるホスト名をマップします。  `BackConnectionHostNames` のレジストリ キーは、通常、ループバック住所にホスト名をマップするために使用されます。  手順は次一覧。  
  
 ループバック住所にマップされ、ローカル コンピュータの Web サイトに接続できるホスト名を指定するには、次の手順に従います。:  
  
 1.  \[スタート\] ボタンをクリックし、\[ファイル名を指定して実行\] をクリックして「regedit」と入力し、\[OK\] をクリックします。  
  
 2.  レジストリ エディターで、次のレジストリ キーを指定して、をクリックします:  
  
 `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa\MSV1_0`  
  
 3.  MSV1\_0 を右クリックし、新しいをポイントして、を複数の文字列の値をクリックします。  
  
 4.  「`BackConnectionHostNames`」と入力して、Enter キーを押します。  
  
 5.  `BackConnectionHostNames`を右クリックし、変更をクリックします。  
  
 6.  値のデータではローカル コンピュータにある入力し、OK をクリックします。入力します。、のホスト名を拠点サービス \(要求の URL で使用されるホスト名\)。  
  
 7.  レジストリ エディターを従業員が退職、を IISAdmin のサービスおよび実行 IISReset を再起動します。  
  
 より、安全な作業はループバックの小切手の説明に [http:\/\/support.microsoft.com\/kb\/896861](http://go.microsoft.com/fwlink/?LinkID=179657)従って無効にすることです。  これは、反映されるの攻撃への対策を無効にします。  したがって、機械が実際に使用する予定だけに代替名のセットを強いることをお勧めします。  
  
## 参照  
 <xref:System.Net.AuthenticationManager.CustomTargetNameDictionary%2A?displayProperty=fullName>   
 <xref:System.Net.HttpRequestHeader?displayProperty=fullName>   
 <xref:System.Net.HttpWebRequest.Host%2A?displayProperty=fullName>