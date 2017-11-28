---
title: "暗号スキームの作成"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- encryption [.NET Framework], creating cryptographic schemes
- cryptography [.NET Framework], creating cryptographic schemes
ms.assetid: d40c509f-5a5e-46cc-94cb-a951e9ab6843
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3e3c4a832f70fae7808bf71016cb9f6648332f01
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="creating-a-cryptographic-scheme"></a>暗号スキームの作成
.NET Framework の暗号化コンポーネントを組み合わせて、データの暗号化と復号化を行うさまざまなスキームを作成することができます。  
  
 データの暗号化と復号化の単純な暗号スキームでは、次の手順を指定することがあります。  
  
1.  暗号化側と復号化側は、公開キーと秘密キーのペアを生成する。  
  
2.  暗号化側と復号化側は、公開キーを交換する。  
  
3.  暗号化側と復号化側は、たとえば TripleDES 暗号化の秘密キーを生成する。続いて、相手側の公開キーを使用して新規作成されたキーを暗号化する。  
  
4.  暗号化側と復号化側は、相手側にデータを送信し、特定の順序で相手側の秘密キーを自分の秘密キーと組み合わせて、新しい秘密キーを作成する。  
  
5.  暗号化側と復号化側は、対称暗号化を使って会話を開始する。  
  
 暗号スキームの作成は簡単な作業ではありません。 暗号化の使用の詳細については、http://msdn.microsoft.com/library のプラットフォーム SDK ドキュメントにある「暗号化」トピックを参照してください。  
  
## <a name="see-also"></a>関連項目  
 [Cryptographic Services](../../../docs/standard/security/cryptographic-services.md)
