---
title: '方法 : サービスのインスタンス化を制御する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e0b12b34-8004-443a-a46d-83a5c00f2601
ms.openlocfilehash: 2f9e4f298eb95498ec8d3603624763bfd95bfda1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-control-service-instancing"></a>方法 : サービスのインスタンス化を制御する
サービスのインスタンス モードを設定することにより、<xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> (およびそのユーザー定義のサービス オブジェクト) をいつ生成するかを指定できます。 設定できるモードについては、<xref:System.ServiceModel.InstanceContextMode> 列挙体を参照してください。 動作に関する詳細については、次を参照してください。[を構成すると、ランタイムのビヘイビアーの使用を拡張する](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)です。 実施例については、次を参照してください。[動作](../../../../docs/framework/wcf/samples/behaviors.md)です。  
  
### <a name="to-control-the-service-instance-lifetime-using-code"></a>サービス インスタンスの有効期間をコードで制御するには  
  
1.  サービス クラスに <xref:System.ServiceModel.ServiceBehaviorAttribute> 属性を適用します。  
  
2.  <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> プロパティを <xref:System.ServiceModel.InstanceContextMode.PerCall>、<xref:System.ServiceModel.InstanceContextMode.PerSession>、<xref:System.ServiceModel.InstanceContextMode.Single> のいずれかの値に設定します。  
  
     [!code-csharp[C_ControlServiceInstancing#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_controlserviceinstancing/cs/source.cs#1)]
     [!code-vb[C_ControlServiceInstancing#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_controlserviceinstancing/vb/source.vb#1)]  
  
## <a name="example"></a>例  
 <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> 属性の <xref:System.ServiceModel.ServiceBehaviorAttribute> プロパティを <xref:System.ServiceModel.InstanceContextMode.PerCall> に設定するコード例を示します。  
  
 [!code-csharp[c_ControlServiceInstancing#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_controlserviceinstancing/cs/source.cs#2)]
 [!code-vb[c_ControlServiceInstancing#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_controlserviceinstancing/vb/source.vb#2)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.ServiceBehaviorAttribute>  
 <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>  
 <xref:System.ServiceModel.InstanceContextMode>  
 [サービス: 動作のサンプル](http://msdn.microsoft.com/library/4e3c6513-a7ff-4b35-8dcf-b5506c6f39a7)
