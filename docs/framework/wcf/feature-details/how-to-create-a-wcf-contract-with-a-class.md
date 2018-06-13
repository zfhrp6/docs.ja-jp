---
title: '方法 : クラスを使用して Windows Communication Foundation コントラクトを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1ad69393-3915-4e7f-9b91-b6fc59c6f5ba
ms.openlocfilehash: 296f500532040aaebf0f6d7d37a7a9aae99a3451
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33491814"
---
# <a name="how-to-create-a-windows-communication-foundation-contract-with-a-class"></a>方法 : クラスを使用して Windows Communication Foundation コントラクトを作成する
インターフェイスを使用しては、Windows Communication Foundation (WCF) コントラクトを作成することをお勧めします。 詳細については、次を参照してください。[する方法: サービス コントラクトを定義する](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)です。 ここで説明する代替方法では、クラスを作成してから、<xref:System.ServiceModel.ServiceContractAttribute> 属性を直接そのクラスに適用し、<xref:System.ServiceModel.OperationContractAttribute> 属性をコントラクトに含まれるクラス内の各メソッドに適用します。  
  
> [!WARNING]
>  `[ServiceContract]` と `[ServiceContractAttribute]` は、同じことを行います。 `[OperationContract]` と `[OperationContractAttribute]` でも、同様です。 いずれの場合も、前者は後者の短縮形です。  
  
 サービス コントラクトの詳細については、次を参照してください。[サービス コントラクトの設計](../../../../docs/framework/wcf/designing-service-contracts.md)です。  
  
### <a name="creating-a-windows-communication-foundation-contract-with-a-class"></a>クラスを使用した Windows Communication Foundation コントラクトの作成  
  
1.  Visual Basic、C# の場合、またはその他の共通言語ランタイム言語を使用して、新しいクラスを作成します。  
  
2.  クラスに <xref:System.ServiceModel.ServiceContractAttribute> クラスを適用します。  
  
3.  クラスでメソッドを作成します。  
  
4.  適用、<xref:System.ServiceModel.OperationContractAttribute>クラス、パブリックの WCF コントラクトの一部として公開する必要がある各メソッドにします。  
  
## <a name="example"></a>例  
 次のコード例は、サービス コントラクトを定義するクラスを示しています。  
  
 [!code-csharp[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithclass/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithclass/vb/source.vb#1)]  
  
 <xref:System.ServiceModel.OperationContractAttribute> クラスが適用されたメソッドは、既定で要求/応答メッセージ パターンを使用します。 このメッセージ パターンの詳細については、次を参照してください。[する方法: 要求/応答コントラクトを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md)です。 属性のプロパティを設定することにより、他のメッセージ パターンを作成および使用できるようになります。 例については、次を参照してください。[する方法: 一方向コントラクトを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md)と[する方法: 双方向コントラクトを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>
