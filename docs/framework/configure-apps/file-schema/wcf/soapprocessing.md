---
title: '&lt;soapProcessing&gt;'
ms.date: 03/30/2017
ms.assetid: e8707027-e6b8-4539-893d-3cd7c13fbc18
ms.openlocfilehash: cc720c9e3a8ab934ffa8d3cb0c6eceb47a708fb1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="ltsoapprocessinggt"></a>&lt;soapProcessing&gt;

異なるバインディングの種類およびメッセージ バージョンの間でメッセージのマーシャリングに使用されるクライアント エンドポイントの動作を定義します。

**\<システムです。ServiceModel >**   
&nbsp;&nbsp;**\<ビヘイビアー >**   
&nbsp;&nbsp;&nbsp;&nbsp;**\<endpointBehaviors >**   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<動作 >**   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<soapProcessing >**

## <a name="syntax"></a>構文

```xml
<soapProcessing processMessages="true|false" />
```

## <a name="attributes-and-elements"></a>属性と要素

以降のセクションでは、属性、子要素、および親要素について説明します。

### <a name="attributes"></a>属性

|                   | 説明 |
| ----------------- | ----------- |
| `processMessages` | SOAP メッセージ バージョン間のメッセージをマーシャリングするかどうかを指定するブール値。 |

### <a name="child-elements"></a>子要素

なし

### <a name="parent-elements"></a>親要素

|     | 説明 |
| --- | ----------- |
| [**\<動作 >**](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) | エンドポイントの動作を指定します。 |

## <a name="remarks"></a>コメント

SOAP 処理は、メッセージ バージョン間でメッセージが変換されるプロセスです。

Windows Communication Foundation (WCF) ルーティング サービスは、別に、1 つのプロトコルからメッセージを変換できます。 受信メッセージのバージョンと送信メッセージのバージョンが異なる場合、新しいメッセージが正しいバージョンで作成されます。 いずれかからメッセージを処理する<!--zz <xref:System.ServiceModel.Channel.MessageVersion> -->`MessageVersion`別には、着信 WCF メッセージから関連するヘッダー、ボディ部を含む新しい WCF メッセージを構築することによって実現します。 アドレス指定に固有のヘッダーまたはルーター レベルで認識されるヘッダーは、新しい WCF メッセージの作成に使用されません。これらのヘッダーは、異なるバージョンであるか (アドレス指定ヘッダーの場合)、クライアントとルーターの間の通信の一部として処理されているためです。

発信メッセージにヘッダーが配置されるかどうかは、受信チャネル層を介して渡されたと認識されるようにマークされているかどうかによって決まります。 認識されないヘッダー (カスタム ヘッダーなど) は削除されずに送信メッセージにコピーされ、ルーティング サービスを介して渡されます。 メッセージの本文は、送信メッセージにコピーされます。 そして、メッセージは送信チャネルに送信されます。この時点で、すべてのヘッダー、および使用されている通信プロトコル/トランスポートに固有のエンベロープ データが作成され、追加されます。

このような処理手順は、SOAP 処理動作が指定されているときに行われます。 これは、 [ \<soapProcessingExtension >](../../../../../docs/framework/configure-apps/file-schema/wcf/soapprocessing.md)動作は、ルーティング サービスの起動時に、すべてのクライアント (送信) エンドポイントに適用されるエンドポイントの動作です。 既定で、 [\<ルーティング >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md)動作を作成し、新しい[ \<soapProcessingExtension >](../../../../../docs/framework/configure-apps/file-schema/wcf/soapprocessing.md)での動作`processMessages`'éý'`true`ごとクライアントのエンドポイントです。 ルーティング サービスが認識しないプロトコルを使用している場合や既定の処理動作をオーバーライドする場合は、ルーティング サービス全体または特定のエンドポイントにおいて SOAP 処理を無効にできます。  SOAP のすべてのエンドポイントにルーティング サービス全体の処理を無効にする設定、`soapProcessing`の属性、 [\<ルーティング >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md)動作を`false`です。 特定のエンドポイントで SOAP 処理を無効にするには、この動作を使用して `processMessages` 属性を `false` に設定してから、既定の処理コードを実行しないエンドポイントにこの動作をアタッチします。  ときに、 [\<ルーティング >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md)動作は、ルーティング サービスを設定、1 つが既に存在するために、エンドポイントの動作を再適用はスキップされます。
