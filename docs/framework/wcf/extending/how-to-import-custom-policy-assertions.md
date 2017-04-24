---
title: "方法 : カスタム ポリシー アサーションをインポートする | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1f41d787-accb-4a10-bfc6-a807671d1581
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# 方法 : カスタム ポリシー アサーションをインポートする
ポリシー アサーションはサービス エンドポイントの機能と要件を説明します。  クライアント アプリケーションはサービス メタデータにあるポリシー アサーションを使用して、クライアント バインディングを構成したり、サービス エンドポイントのサービス コントラクトをカスタマイズしたりできます。  
  
 実装することによってカスタム ポリシー アサーションのインポート、 <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=fullName>インターフェイスとをメタデータ システム、または実装を登録することによって、そのオブジェクトを渡すことが、アプリケーション構成ファイルに入力します。  実装、 <xref:System.ServiceModel.Description.IPolicyImportExtension>インターフェイスは、既定のコンス トラクターを提供する必要があります。  
  
### <a name="to-import-custom-policy-assertions"></a>カスタム ポリシー アサーションをインポートするには  
  
1.  実装、 <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=fullName>クラスのインターフェイスです。 次の手順を参照してください。  
  
2.  次のいずれかの方法でカスタム ポリシー インポーターを挿入します。  
  
3.  構成ファイルを使用します。 次の手順を参照してください。  
  
4.  構成ファイルを使用して[ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)します。 次の手順を参照してください。  
  
5.  プログラムでポリシー インポーターを挿入します。 次の手順を参照してください。  
  
### <a name="to-implement-the-systemservicemodeldescriptionipolicyimportextension-interface-on-any-class"></a>任意のクラスに System.ServiceModel.Description.IPolicyImportExtension インターフェイスを実装するには  
  
1.  <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=fullName>メソッドで、関心のある対象各ポリシーについてポリシー アサーションを見つけます (するアサーションのスコープに応じて) 適切なメソッドを呼び出して、インポートするには<xref:System.ServiceModel.Description.PolicyConversionContext?displayProperty=fullName>メソッドに渡されるオブジェクト。 次のコード例を使用する方法を示しています、 <xref:System.ServiceModel.Description.PolicyAssertionCollection.Remove%2A?displayProperty=fullName>メソッドは、カスタム ポリシー アサーションの検索を&1; つの手順でコレクションから削除します。 remove メソッドを使用してアサーションの検索と削除を行う場合は、手順 4. を実行する必要はありません。  
  
     [!code-csharp[CustomPolicySample#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/policyimporter.cs#9)]
     [!code-vb[CustomPolicySample#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/custompolicysample/vb/policyimporter.vb#9)]  
  
2.  ポリシー アサーションを処理します。 ポリシー システムでは、入れ子になったポリシーと `wsp:optional` を正規化しないので注意してください。 これらの構造体については、ポリシー インポート拡張機能の実装で処理する必要があります。  
  
3.  ポリシー アサーションで指定されている機能または要件をサポートするバインディングまたはコントラクトのカスタマイズを実行します。 アサーションでは、通常、バインディングに特定の構成、または特定のバインド要素が必要です。 アクセスすることによってこの変更を行う、 <xref:System.ServiceModel.Description.PolicyConversionContext.BindingElements%2A?displayProperty=fullName>プロパティです。 これとは別に、コントラクトの変更が必要なアサーションがあります。  アクセスしを使用してコントラクトを変更することができます、 <xref:System.ServiceModel.Description.PolicyConversionContext.Contract%2A?displayProperty=fullName>プロパティです。  ポリシー代替手段のインポートに失敗した場合、バインディングとコントラクトは同じなのに、ポリシー代替手段が異なるために、ポリシー インポーターが複数回呼び出されることがあるので注意してください。 作成するコードでは、この動作に対応する必要があります。  
  
4.  アサーション コレクションからカスタム ポリシー アサーションを削除します。 アサーションを削除しない場合、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] は、ポリシーのインポートが失敗して、関連付けられているバインディングがインポートされていないと見なします。 使用した場合、 <xref:System.ServiceModel.Description.PolicyAssertionCollection.Remove%2A?displayProperty=fullName>メソッドをカスタム ポリシー アサーションを見つけて、この手順を実行しなくても&1; つの手順でコレクションから削除します。  
  
### <a name="to-insert-the-custom-policy-importer-into-the-metadata-system-using-a-configuration-file"></a>構成ファイルを使用してメタデータ システムにカスタム ポリシー インポーターを挿入するには  
  
1.  インポーター型を追加、`<extensions>`内の要素、 [ <> \> ](../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md)クライアント構成ファイル内の要素。  
  
     <!-- TODO: review snippet reference [!code[CustomPolicySample#7](../../../../samples/snippets/common/VS_Snippets_CFX/custompolicysample/common/client.exe.config#7)]  -->
     <!-- TODO: review snippet reference [!code-csharp[CustomPolicySample#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/client.exe.config#7)]  -->
     <!-- TODO: review snippet reference [!code-vb[CustomPolicySample#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/custompolicysample/vb/client.exe.config#7)]  -->  
  
2.  クライアント アプリケーションで使用して、 <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=fullName>または<xref:System.ServiceModel.Description.WsdlImporter?displayProperty=fullName>を解決するには、メタデータと、インポーターが自動的に呼び出されます。  
  
     [!code-csharp[CustomPolicySample#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/client.cs#10)]
     [!code-vb[CustomPolicySample#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/custompolicysample/vb/client.vb#10)]  
  
### <a name="to-insert-the-custom-policy-importer-into-the-metadata-system-using-svcutilexe"></a>Svcutil.exe を使用してメタデータ システムにカスタム ポリシー インポーターを挿入するには  
  
1.  インポーター型を追加、`<extensions>`内の要素、 [ <> \> ](../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md) Svcutil.exe.config 構成ファイル内の要素。 また、`/svcutilConfig` オプションを使用して、異なる構成ファイルに登録されているポリシー インポーター型を読み込むように Svcutil.exe を指定することもできます。  
  
2.  使用[ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)メタデータと、インポーターをインポートするのには、自動的に呼び出されます。  
  
### <a name="to-insert-the-custom-policy-importer-into-the-metadata-system-programmatically"></a>プログラム使用してメタデータ システムにカスタム ポリシー インポーターを挿入するには  
  
1.  インポーターを追加、 <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A?displayProperty=fullName>プロパティ (を使用している場合など、 <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=fullName>) メタデータをインポートする前にします。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=fullName>   
 <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=fullName>   
 <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=fullName>   
 [メタデータ システムの拡張](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md)