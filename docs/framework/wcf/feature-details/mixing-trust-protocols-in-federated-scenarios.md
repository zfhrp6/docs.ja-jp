---
title: "Trust プロトコルが混在するフェデレーション シナリオ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d7b5fee9-2246-4b09-b8d7-9e63cb817279
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 007dec81766423ea2826e98ae0b6b399a1508f11
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="mixing-trust-protocols-in-federated-scenarios"></a>Trust プロトコルが混在するフェデレーション シナリオ
シナリオによっては、フェデレーション クライアントが、Trust バージョンの一致しないサービスやセキュリティ トークン サービス (STS: Security Token Service) と通信する場合があります。 たとえば、サービス WSDL に、STS とは異なるバージョンの WS-Trust 要素を持つ `RequestSecurityTokenTemplate` アサーションが含まれることがあります。 このような場合、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] クライアントは、`RequestSecurityTokenTemplate` から受け取った WS-Trust 要素を、STS Trust のバージョンに一致するように変換します。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、標準バインディングでのみ不一致の Trust バージョンを処理します。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] によって認識されるすべての標準アルゴリズム パラメーターは、標準バインディングの一部です。 このトピックでは、サービスと STS との間のさまざまな Trust 設定での [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の動作について説明します。  
  
## <a name="rp-feb-2005-and-sts-feb-2005"></a>RP 2005/02 および STS 2005/02  
 証明書利用者 (RP: Relying Party) の WSDL には、`RequestSecurityTokenTemplate` セクション内に次の要素が含まれます。  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
 クライアント構成ファイルには、パラメーターのリストが含まれます。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、クライアント パラメーターとサービス パラメーターを区別することはできません。すべてのパラメーターが追加され、`RequestSecurityTokenTemplate` (RST) で送信されます。  
  
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
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]、`EncryptionAlgorithm`、および `CanonicalizationAlgorithm` の各要素が `KeyWrapAlgorithm` 要素の中に存在する場合、`SecondaryParameters` はこれらを RST の最上位の要素から削除します。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、`SecondaryParameters` 要素を変更せずに送信 RST に追加します。  
  
## <a name="rp-trust-feb-2005-and-sts-trust-13"></a>RP Trust 2005/02 および STS Trust 1.3  
 RP の WSDL には、`RequestSecurityTokenTemplate` セクション内に次の要素が含まれます。  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
 クライアント構成ファイルには、パラメーターのリストが含まれます。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、クライアント構成ファイルからサービス パラメーターとクライアント パラメーターを区別することはできません。 このため、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、すべてのパラメーターを Trust バージョン 1.3 の名前空間に変換します。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、`KeyType`、`KeySize`、および `TokenType` の各要素を次のように処理します。  
  
-   WSDL をダウンロードし、バインディングを作成して、`KeyType`、`KeySize`、および `TokenType` を RP パラメーターから割り当てます。 その後、クライアント構成ファイルが生成されます。  
  
-   この時点で、クライアントは構成ファイル内のパラメーターを変更できます。  
  
-   実行時には、指定されたすべてのパラメーターが、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] によってクライアント構成ファイルの `AdditionalTokenParameters` セクションにコピーされます。ただし、`KeyType`、`KeySize`、および `TokenType` は構成ファイルの生成時に処理されるため、これらのパラメーターのコピーは行われません。  
  
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
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、`SecondaryParameters` セクション内に指定されたすべてのパラメーターを最上位の RST 要素にコピーしますが、2005 WS-Trust の名前空間には変換しません。
