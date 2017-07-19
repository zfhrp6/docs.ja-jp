---
title: "JSON シリアル化 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3c2c4747-7510-4bdf-b4fe-64f98428ef4a
caps.latest.revision: 19
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 19
---
# JSON シリアル化
このサンプルでは、<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> を使用して、JavaScript Object Notation \(JSON\) 形式のデータをシリアル化および逆シリアル化する方法を示します。このシリアル化エンジンによって、JSON データを [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 型のインスタンスに変換したり、また JSON データに戻したりできます。<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> では、<xref:System.Runtime.Serialization.DataContractSerializer> と同じ型をサポートしています。JSON データ形式は、特に Asynchronous JavaScript and XML \(AJAX\) スタイルの Web アプリケーションを作成するときに便利です。[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] での AJAX サポートは、ScriptManager コントロールを介して ASP.NET AJAX と共に使用できるように最適化されています。ASP.NET AJAX と共に [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] を使用する例については、「[AJAX Samples](http://msdn.microsoft.com/ja-jp/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e)」を参照してください。  
  
> [!NOTE]
>  このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
 このサンプルでは、シリアル化および逆シリアル化を示すために、`Person` データ コントラクトを使用しています。  
  
```  
[DataContract]  
    class Person  
    {  
        [DataMember]  
        internal string name;  
  
        [DataMember]  
        internal int age;  
    }  
  
```  
  
 `Person` 型のインスタンスを JSON にシリアル化するには、最初に <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> を作成し、次に `WriteObject` メソッドを使用して JSON データをストリームに書き込みます。  
  
```  
Person p = new Person();  
//Set up Person object...  
MemoryStream stream1 = new MemoryStream();  
DataContractJsonSerializer ser = new DataContractJsonSerializer(typeof(Person));  
ser.WriteObject(stream1, p);  
  
```  
  
 メモリ ストリームには有効な JSON データが含まれています。  
  
```  
{“age”:42,”name”:”John”}  
  
```  
  
 このサンプルでは、JSON データからオブジェクトへの逆シリアル化を示します。次に、ストリームを巻き戻し、`ReadObject` を呼び出します。  
  
```  
Person p2 = (Person)ser.ReadObject(stream1);  
```  
  
 `p2` オブジェクトを調べることで、JSON データが正しく逆シリアル化されていることがわかります。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\JsonSerialization`  
  
#### サンプルを設定、ビルド、および実行するには  
  
1.  「[Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)」の説明に従って、ソリューション JsonSerialization.sln をビルドします。  
  
2.  作成されたコンソール アプリケーションを実行します。  
  
## 参照