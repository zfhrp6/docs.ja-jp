---
title: '方法 : XmlSerializer を使用する WCF クライアント アプリケーションの起動時間を短縮する'
ms.date: 03/30/2017
ms.assetid: 21093451-0bc3-4b1a-9a9d-05f7f71fa7d0
ms.openlocfilehash: 6f61c57998cfc21b66f278a1a2381407ec2c39ce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-improve-the-startup-time-of-wcf-client-applications-using-the-xmlserializer"></a>方法 : XmlSerializer を使用する WCF クライアント アプリケーションの起動時間を短縮する
<xref:System.Xml.Serialization.XmlSerializer> を使用してシリアル化できるデータ型を使用するサービスおよびクライアント アプリケーションは、実行時にこのようなデータ型のシリアル化コードを生成およびコンパイルします。このため、起動時のパフォーマンスが低下することがあります。  
  
> [!NOTE]
>  事前生成済みシリアル化コードはクライアント アプリケーションでのみ使用できます。サービスでは使用できません。  
  
 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)アプリケーションのコンパイル済みアセンブリから、必要なシリアル化コードを生成することによってこれらのアプリケーションの起動時のパフォーマンスを向上させることができます。 Svcutil.exe は、<xref:System.Xml.Serialization.XmlSerializer> を使用してシリアル化できるコンパイル済みアプリケーション アセンブリに格納されたサービス コントラクトで使用されるすべてのデータ型に対して、シリアル化コードを生成します。 <xref:System.Xml.Serialization.XmlSerializer> を使用するサービスおよび操作コントラクトは、<xref:System.ServiceModel.XmlSerializerFormatAttribute> でマークされます。  
  
### <a name="to-generate-xmlserializer-serialization-code"></a>XmlSerializer シリアル化コードを生成するには  
  
1.  サービスまたはクライアント コードを 1 つ以上のアセンブリにコンパイルします。  
  
2.  SDK コマンド プロンプトを開きます。  
  
3.  コマンド プロンプトで、次の形式を使用して Svcutil.exe ツールを起動します。  
  
    ```  
    svcutil.exe /t:xmlSerializer  <assemblyPath>*  
    ```  
  
     `assemblyPath` 引数には、サービス コントラクト型を格納するアセンブリへのパスを指定します。 Svcutil.exe は、<xref:System.Xml.Serialization.XmlSerializer> を使用してシリアル化できるコンパイル済みアプリケーション アセンブリに格納されたサービス コントラクトで使用されるすべてのデータ型に対して、シリアル化コードを生成します。  
  
     Svcutil.exe は、C# のシリアル化コードのみを生成できます。 入力アセンブリごとに、1 つのソース コード ファイルが生成されます。 使用することはできません、 **/language**スイッチを生成されたコードの言語を変更します。  
  
     依存アセンブリへのパスを指定するには、使用、 **/reference**オプション。  
  
4.  次のオプションのいずれかを使用して、生成したシリアル化コードをアプリケーションから利用できるようにします。  
  
    1.  名前の別のアセンブリに生成されたシリアル化コードをコンパイル [*元のアセンブリ*] です。XmlSerializers.dll (たとえば、MyApp.XmlSerializers.dll)。 アプリケーションがアセンブリを読み込むことができ、アセンブリが元のアセンブリと同じキーで署名されている必要があります。 元のアセンブリを再コンパイルする場合は、シリアル化アセンブリも再生成する必要があります。  
  
    2.  生成されたシリアル化コードを別個のアセンブリにコンパイルし、<xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> を使用するサービス コントラクトで <xref:System.ServiceModel.XmlSerializerFormatAttribute> を使用します。 <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> プロパティまたは <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> プロパティが、コンパイル済みのシリアル化アセンブリを指すように設定します。  
  
    3.  生成されたシリアル化コードをアプリケーション アセンブリにコンパイルし、<xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> を使用するサービス コントラクトに <xref:System.ServiceModel.XmlSerializerFormatAttribute> を追加します。 <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> プロパティおよび <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> プロパティは設定しないでください。 既定のシリアル化アセンブリが現在のアセンブリであると見なされます。  
  
### <a name="to-generate-xmlserializer-serialization-code-in-visual-studio"></a>Visual Studio で XmlSerializer シリアル化コードを生成するには  
  
1.  Visual Studio で WCF サービスとクライアント プロジェクトを作成します。 次に、クライアント プロジェクトへのサービス参照を追加します。  
  
2.  追加、<xref:System.ServiceModel.XmlSerializerFormatAttribute>にサービス コントラクトを*reference.cs*下クライアント アプリのプロジェクト ファイル**serviceReference** -> **reference.svcmap**. すべてのファイルを表示する必要があります**ソリューション エクスプ ローラー**にこれらのファイルを参照してください。  
  
3.  クライアント アプリをビルドします。  
  
4.  使用して、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)事前に生成されたシリアライザーを作成する *.cs*コマンドを使用して、ファイル。  
  
    ```  
    svcutil.exe /t:xmlSerializer  <assemblyPath>*  
    ```  
  
     AssemblyPath 引数では、WCF クライアント アセンブリへのパスを指定します。  
  
     例を示します。  
  
    ```  
    svcutil.exe /t:xmlSerializer wcfclient.exe  
    ```  
  
     *WCFClient.XmlSerializers.dll.cs*ファイルが生成されます。  
  
5.  生成済みシリアル化アセンブリをコンパイルします。  
  
     上記の例に基づいて、コンパイルのコマンドは次になります。  
  
    ```  
    csc /r:wcfclient.exe /out:WCFClient.XmlSerializers.dll /t:library WCFClient.XmlSerializers.dll.cs  
    ```  
  
     確認、生成された*WCFClient.XmlSerializers.dll*はクライアント アプリケーションと同じディレクトリに*WCFClient.exe*ここでします。  
  
6.  クライアント アプリを通常どおり実行します。 生成済みシリアル化アセンブリが使用されます。  
  
## <a name="example"></a>例  
 次のコマンドにより、アセンブリに含まれているサービス コントラクトが使用する `XmlSerializer` 型用のシリアル化型を生成します。  
  
```  
svcutil /t:xmlserializer myContractLibrary.exe  
```  
  
## <a name="see-also"></a>関連項目  
 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
