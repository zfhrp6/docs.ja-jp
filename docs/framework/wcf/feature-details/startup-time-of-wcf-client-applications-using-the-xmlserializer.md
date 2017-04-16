---
title: "方法 : XmlSerializer を使用する WCF クライアント アプリケーションの起動時間を短縮する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 21093451-0bc3-4b1a-9a9d-05f7f71fa7d0
caps.latest.revision: 13
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# 方法 : XmlSerializer を使用する WCF クライアント アプリケーションの起動時間を短縮する
<xref:System.Xml.Serialization.XmlSerializer> を使用してシリアル化できるデータ型を使用するサービスおよびクライアント アプリケーションは、実行時にこのようなデータ型のシリアル化コードを生成およびコンパイルします。このため、起動時のパフォーマンスが低下することがあります。  
  
> [!NOTE]
>  事前生成済みシリアル化コードはクライアント アプリケーションでのみ使用できます。サービスでは使用できません。  
  
 [ServiceModel メタデータ ユーティリティ ツール \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) を使用すると、必要なシリアル化コードをアプリケーションのコンパイル済みアセンブリから生成することで、このようなアプリケーションの起動時のパフォーマンスを改善できます。Svcutil.exe は、<xref:System.Xml.Serialization.XmlSerializer> を使用してシリアル化できるコンパイル済みアプリケーション アセンブリに格納されたサービス コントラクトで使用されるすべてのデータ型に対して、シリアル化コードを生成します。<xref:System.Xml.Serialization.XmlSerializer> を使用するサービスおよび操作コントラクトは、<xref:System.ServiceModel.XmlSerializerFormatAttribute> でマークされます。  
  
### XmlSerializer シリアル化コードを生成するには  
  
1.  サービスまたはクライアント コードを 1 つ以上のアセンブリにコンパイルします。  
  
2.  SDK コマンド プロンプトを開きます。  
  
3.  コマンド プロンプトで、次の形式を使用して Svcutil.exe ツールを起動します。  
  
    ```  
    svcutil.exe /t:xmlSerializer  <assemblyPath>*  
    ```  
  
     `assemblyPath` 引数には、サービス コントラクト型を格納するアセンブリへのパスを指定します。Svcutil.exe は、<xref:System.Xml.Serialization.XmlSerializer> を使用してシリアル化できるコンパイル済みアプリケーション アセンブリに格納されたサービス コントラクトで使用されるすべてのデータ型に対して、シリアル化コードを生成します。  
  
     Svcutil.exe は、C\# のシリアル化コードのみを生成できます。入力アセンブリごとに、1 つのソース コード ファイルが生成されます。生成されるコードの言語を変更するために、**\/language** スイッチを使用することはできません。  
  
     依存アセンブリへのパスを指定するには、**\/reference** オプションを使用します。  
  
4.  次のオプションのいずれかを使用して、生成したシリアル化コードをアプリケーションから利用できるようにします。  
  
    1.  生成されたシリアル化コードを \[*original assembly*\].XmlSerializers.dll という名前 \(たとえば、MyApp.XmlSerializers.dll\) で別個のアセンブリにコンパイルします。アプリケーションがアセンブリを読み込むことができ、アセンブリが元のアセンブリと同じキーで署名されている必要があります。元のアセンブリを再コンパイルする場合は、シリアル化アセンブリも再生成する必要があります。  
  
    2.  生成されたシリアル化コードを別個のアセンブリにコンパイルし、<xref:System.ServiceModel.XmlSerializerFormatAttribute> を使用するサービス コントラクトで <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> を使用します。<xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> プロパティまたは <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> プロパティが、コンパイル済みのシリアル化アセンブリを指すように設定します。  
  
    3.  生成されたシリアル化コードをアプリケーション アセンブリにコンパイルし、<xref:System.ServiceModel.XmlSerializerFormatAttribute> を使用するサービス コントラクトに <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> を追加します。<xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> プロパティおよび <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> プロパティは設定しないでください。既定のシリアル化アセンブリが現在のアセンブリであると見なされます。  
  
## 使用例  
 次のコマンドにより、アセンブリに含まれているサービス コントラクトが使用する `XmlSerializer` 型用のシリアル化型を生成します。  
  
```  
svcutil /t:xmlserializer myContractLibrary.exe  
```  
  
## 参照  
 [ServiceModel メタデータ ユーティリティ ツール \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)