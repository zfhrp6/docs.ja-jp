---
title: Trust プロトコルが混在するフェデレーション シナリオ
ms.date: 03/30/2017
ms.assetid: d7b5fee9-2246-4b09-b8d7-9e63cb817279
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: bca23ba16c69c6d21ed7cf49aaebb8d2ed079f5e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="mixing-trust-protocols-in-federated-scenarios"></a>Trust プロトコルが混在するフェデレーション シナリオ
シナリオによっては、フェデレーション クライアントが、Trust バージョンの一致しないサービスやセキュリティ トークン サービス (STS: Security Token Service) と通信する場合があります。 たとえば、サービス WSDL に、STS とは異なるバージョンの WS-Trust 要素を持つ `RequestSecurityTokenTemplate` アサーションが含まれることがあります。 このような場合は、Windows Communication Foundation (WCF) クライアントから受け取った Ws-trust 要素に変換します、 `RequestSecurityTokenTemplate` STS trust のバージョンと一致します。 WCF では、標準バインディングでのみ不一致の trust バージョンを処理します。 WCF で認識されるすべての標準アルゴリズム パラメーターは、標準バインディングの一部です。 このトピックでは、さまざまな信頼の設定、サービスと STS との間での WCF 動作について説明します。  
  
## <a name="rp-feb-2005-and-sts-feb-2005"></a>RP 2005/02 および STS 2005/02  
 証明書利用者 (RP: Relying Party) の WSDL には、`RequestSecurityTokenTemplate` セクション内に次の要素が含まれます。  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
 クライアント構成ファイルには、パラメーターのリストが含まれます。  
  
 WCF は、クライアントとサービスのパラメーターを区別できません。すべてのパラメーターを追加で送信され、 `RequestSecurityTokenTemplate` (RST)。  
  
## <a name="rp-trust-13-and-sts-trust-13"></a>RP Trust 1.3 および STS Trust 1.3  
 RP の WSDL には、`RequestSecurityTokenTemplate` セクション内に次の要素が含まれます。  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
-   `KeyWrapAlgorithm`  
  
 クライアント構成ファイルには、RP によって指定されたパラメーターをラップする `secondaryParameters` 要素が含まれます。  
  
 WCF の削除、 `EncryptionAlgorithm`、`CanonicalizationAlgorithm`と`KeyWrapAlgorithm`RST これらの中に存在する場合、最上位の要素からの要素、`SecondaryParameters`要素。 WCF の追加、`SecondaryParameters`くだ送信 RST 要素。  
  
## <a name="rp-trust-feb-2005-and-sts-trust-13"></a>RP Trust 2005/02 および STS Trust 1.3  
 RP の WSDL には、`RequestSecurityTokenTemplate` セクション内に次の要素が含まれます。  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
 クライアント構成ファイルには、パラメーターのリストが含まれます。  
  
 クライアント構成ファイルから WCF は、サービスとクライアント パラメーターを区別できません。 したがって WCF では、すべてのパラメーターが信頼バージョン 1.3 の名前空間に変換します。  
  
 WCF ハンドル、 `KeyType`、 `KeySize`、および`TokenType`要素は次のようにします。  
  
-   WSDL をダウンロードし、バインディングを作成して、`KeyType`、`KeySize`、および `TokenType` を RP パラメーターから割り当てます。 その後、クライアント構成ファイルが生成されます。  
  
-   この時点で、クライアントは構成ファイル内のパラメーターを変更できます。  
  
-   実行時に WCF コピーに指定されたすべてのパラメーター、 `AdditionalTokenParameters` 、クライアント構成ファイルのセクションを除く`KeyType`、`KeySize`と`TokenType`これらのパラメーターは、構成ファイル中に考慮するため、生成します。  
  
## <a name="rp-trust-13-and-sts-trust-feb-2005"></a>RP Trust 1.3 および STS Trust 2005/02  
 RP の WSDL には、`RequestSecurityTokenTemplate` セクション内に次の要素が含まれます。  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
-   `KeyWrapAlgorithm`  
  
 クライアント構成ファイルには、RP によって指定されたパラメーターをラップする `secondaryParamters` 要素が含まれます。  
  
 WCF コピー内で指定されたすべてのパラメーター、 `SecondaryParameters` RST の最上位の要素のセクションは、2005 Ws-trust 名前空間に変換しません。
