---
title: "POCO サポート | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3846ca73-2819-4ca2-8367-dc739dde5a5b
caps.latest.revision: 11
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 11
---
# POCO サポート
このサンプルでは、マークされていない型 \(シリアル化属性が適用されていない型で、POCO \(Plain Old CLR Object\) 型と呼ばれる場合もあります\) のシリアル化のサポートについて説明します。<xref:System.Runtime.Serialization.DataContractSerializer> では、既定のコンストラクタを持つすべてのマークされていないパブリック型について、データ コントラクトを推測します。データ コントラクトを使用すると、サービスと構造化データをやり取りできます。マークされていない型[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[シリアル化可能な型](../../../../docs/framework/wcf/feature-details/serializable-types.md)」を参照してください。  
  
 このサンプルは[概要](../../../../docs/framework/wcf/samples/getting-started-sample.md)に基づいていますが、プリミティブ数値型ではなく複素数を使用します。また、<xref:System.Runtime.Serialization.DataContractAttribute> 属性と <xref:System.Runtime.Serialization.DataMemberAttribute> 属性が使用されない点を除いて、[基本的なデータ コントラクト](../../../../docs/framework/wcf/samples/basic-data-contract.md)のサンプルにも類似しています。  
  
 サービスはインターネット インフォメーション サービス \(IIS\) によってホストされています。クライアントはコンソール アプリケーション \(.exe\) です。  
  
> [!NOTE]
>  このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
 `ComplexNumber` クラスは、`ServiceContract` で使用されます。次のサンプル コードに示すように、`ComplexNumber` 型には、<xref:System.Runtime.Serialization.DataContractAttribute> 属性と <xref:System.Runtime.Serialization.DataMemberAttribute> 属性がありません。既定では、パブリック プロパティとパブリック フィールドはすべてシリアル化されます。  
  
```  
public class ComplexNumber  
{  
    public double Real;  
    public double Imaginary;  
    public ComplexNumber()  
    {  
        Real = double.MinValue;  
        Imaginary = double.MinValue;  
    }  
    public ComplexNumber(double real, double imaginary)  
    {  
        this.Real = real;  
        this.Imaginary = imaginary;  
    }  
}  
```  
  
### サンプルを設定、ビルド、および実行するには  
  
1.  「[Windows Communication Foundation サンプルの 1 回限りのセットアップの手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)」が実行済みであることを確認します。  
  
2.  ソリューションの C\# 版または Visual Basic .NET 版をビルドするには、「[Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
3.  単一コンピューター構成か複数コンピューター構成かに応じて、「[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)」の手順に従います。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\POCO`  
  
## 参照  
 <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>   
 [シリアル化可能な型](../../../../docs/framework/wcf/feature-details/serializable-types.md)