---
title: '方法 : Svcutil.exe を使用してコンパイル済みのサービス コードからメタデータをエクスポートする'
ms.date: 03/30/2017
ms.assetid: 95d0aed3-16a2-4398-89bb-39418eeb7355
ms.openlocfilehash: 68d651a396aa748d53f9121e9861260bdbf2dffa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-svcutilexe-to-export-metadata-from-compiled-service-code"></a><span data-ttu-id="f5f4c-102">方法 : Svcutil.exe を使用してコンパイル済みのサービス コードからメタデータをエクスポートする</span><span class="sxs-lookup"><span data-stu-id="f5f4c-102">How to: Use Svcutil.exe to Export Metadata from Compiled Service Code</span></span>
<span data-ttu-id="f5f4c-103">Svcutil.exe は、次のように、コンパイル済みアセンブリのサービス、コントラクト、およびデータ型のメタデータをエクスポートできます。</span><span class="sxs-lookup"><span data-stu-id="f5f4c-103">Svcutil.exe can export metadata for services, contracts, and data types in compiled assemblies, as follows:</span></span>  
  
-   <span data-ttu-id="f5f4c-104">Svcutil.exe を使用して、アセンブリのセットに対するすべてのコンパイル済みサービス コントラクトのメタデータをエクスポートするには、入力パラメーターとして各アセンブリを指定します。</span><span class="sxs-lookup"><span data-stu-id="f5f4c-104">To export metadata for all compiled service contracts for a set of assemblies using Svcutil.exe, specify the assemblies as input parameters.</span></span> <span data-ttu-id="f5f4c-105">これが既定の動作です。</span><span class="sxs-lookup"><span data-stu-id="f5f4c-105">This is the default behavior.</span></span>  
  
-   <span data-ttu-id="f5f4c-106">Svcutil.exe を使用して、コンパイル済みサービスのメタデータをエクスポートするには、入力パラメーターとしてサービス アセンブリを指定します。</span><span class="sxs-lookup"><span data-stu-id="f5f4c-106">To export metadata for a compiled service using Svcutil.exe, specify the service assembly or assemblies as input parameters.</span></span> <span data-ttu-id="f5f4c-107">`/serviceName` オプションを使用して、エクスポートするサービスの構成名を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f5f4c-107">You must use the `/serviceName` option to indicate the configuration name of the service you want to export.</span></span> <span data-ttu-id="f5f4c-108">Svcutil.exe を実行すると、指定した実行可能アセンブリの構成ファイルが自動的に読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="f5f4c-108">Svcutil.exe automatically loads the configuration file for the specified executable assembly.</span></span>  
  
-   <span data-ttu-id="f5f4c-109">アセンブリ セットのすべてのデータ コントラクト型をエクスポートするには、`/dataContractOnly` オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="f5f4c-109">To export all data contract types within a set of assemblies, use the `/dataContractOnly` option.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f5f4c-110">`/reference` オプションを使用して、任意の依存アセンブリへのファイル パスを指定してください。</span><span class="sxs-lookup"><span data-stu-id="f5f4c-110">Use the `/reference` option to specify the file paths to any dependent assemblies.</span></span>  
  
### <a name="to-export-metadata-for-compiled-service-contracts"></a><span data-ttu-id="f5f4c-111">コンパイル済みサービス コントラクトのメタデータをエクスポートするには</span><span class="sxs-lookup"><span data-stu-id="f5f4c-111">To export metadata for compiled service contracts</span></span>  
  
1.  <span data-ttu-id="f5f4c-112">サービス コントラクトの実装を 1 つ以上のクラス ライブラリにコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="f5f4c-112">Compile your service contract implementations into one or more class libraries.1</span></span>  
  
2.  <span data-ttu-id="f5f4c-113">コンパイルされたアセンブリに対して Svcutil.exe を実行します。</span><span class="sxs-lookup"><span data-stu-id="f5f4c-113">Run Svcutil.exe on the compiled assemblies.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f5f4c-114">依存アセンブリへのファイル パスを指定するには、`/reference` スイッチを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f5f4c-114">You might need to use the `/reference` switch to specify the file path to any dependent assemblies.</span></span>  
  
    ```  
    svcutil.exe Contracts.dll  
    ```  
  
### <a name="to-export-metadata-for-a-compiled-service"></a><span data-ttu-id="f5f4c-115">コンパイル済みサービスのメタデータをエクスポートするには</span><span class="sxs-lookup"><span data-stu-id="f5f4c-115">To export metadata for a compiled service</span></span>  
  
1.  <span data-ttu-id="f5f4c-116">サービスの実装を実行可能アセンブリにコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="f5f4c-116">Compile your service implementation into an executable assembly.</span></span>  
  
2.  <span data-ttu-id="f5f4c-117">サービス実行可能ファイルの構成ファイルを作成し、サービス構成を追加します。</span><span class="sxs-lookup"><span data-stu-id="f5f4c-117">Create a configuration file for your service executable and add a service configuration.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.serviceModel>  
        <services>  
          <service name="MyService" >  
            <endpoint address="finder" contract="IPeopleFinder" binding="wsHttpBinding" />  
          </service>  
        </services>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
3.  <span data-ttu-id="f5f4c-118">コンパイルされたサービス実行可能ファイルに対して Svcutil.exe を実行します。その際、`/serviceName` スイッチを使用してサービスの構成名を指定してください。</span><span class="sxs-lookup"><span data-stu-id="f5f4c-118">Run Svcutil.exe on the compiled service executable using the `/serviceName` switch to specify the configuration name of the service.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f5f4c-119">依存アセンブリへのファイル パスを指定するには、`/reference` スイッチを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f5f4c-119">You might need to use the `/reference` switch to specify the file path to any dependent assemblies.</span></span>  
  
    ```  
    svcutil.exe /serviceName:MyService Service.exe /reference:path/Contracts.dll  
    ```  
  
### <a name="to-export-metadata-for-compiled-data-contracts"></a><span data-ttu-id="f5f4c-120">コンパイル済みデータ コントラクトのメタデータをエクスポートするには</span><span class="sxs-lookup"><span data-stu-id="f5f4c-120">To export metadata for compiled data contracts</span></span>  
  
1.  <span data-ttu-id="f5f4c-121">データ コントラクトの実装を 1 つ以上のクラス ライブラリにコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="f5f4c-121">Compile your data contract implementations into one or more class libraries.</span></span>  
  
2.  <span data-ttu-id="f5f4c-122">コンパイルされたアセンブリに対して Svcutil.exe を実行します。その際、`/dataContract` スイッチを使用して、データ コントラクトのメタデータだけが生成されるように指定してください。</span><span class="sxs-lookup"><span data-stu-id="f5f4c-122">Run Svcutil.exe on the compiled assemblies using the `/dataContract` switch to specify that only metadata for data contracts should be generated.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f5f4c-123">依存アセンブリへのファイル パスを指定するには、`/reference` スイッチを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f5f4c-123">You might need to use the `/reference` switch to specify the file path to any dependent assemblies.</span></span>  
  
    ```  
    svcutil.exe /dataContractOnly Contracts.dll  
    ```  
  
## <a name="example"></a><span data-ttu-id="f5f4c-124">例</span><span class="sxs-lookup"><span data-stu-id="f5f4c-124">Example</span></span>  
 <span data-ttu-id="f5f4c-125">単純なサービス実装および構成のメタデータを生成する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="f5f4c-125">The following example demonstrates how to generate metadata for a simple service implementation and configuration.</span></span>  
  
 <span data-ttu-id="f5f4c-126">サービス コントラクトのメタデータをエクスポートするには、次のように指定します。</span><span class="sxs-lookup"><span data-stu-id="f5f4c-126">To export metadata for the service contract.</span></span>  
  
```  
svcutil.exe Contracts.dll  
```  
  
 <span data-ttu-id="f5f4c-127">データ コントラクトのメタデータをエクスポートするには、次のように指定します。</span><span class="sxs-lookup"><span data-stu-id="f5f4c-127">To export metadata for the data contracts.</span></span>  
  
```  
svcutil.exe /dataContractOnly Contracts.dll  
```  
  
 <span data-ttu-id="f5f4c-128">サービス実装のメタデータをエクスポートするには、次のように指定します。</span><span class="sxs-lookup"><span data-stu-id="f5f4c-128">To export metadata for the service implementation.</span></span>  
  
```  
svcutil.exe /serviceName:MyService Service.exe /reference:<path>/Contracts.dll  
```  
  
 <span data-ttu-id="f5f4c-129">`<path>` は Contracts.dll へのパスです。</span><span class="sxs-lookup"><span data-stu-id="f5f4c-129">The `<path>` is the path to Contracts.dll.</span></span>  
  
```  
// The following service contract and data contracts are compiled into   
// Contracts.dll.  
[ServiceContract(ConfigurationName="IPeopleFinder")]  
public interface IPersonFinder  
{  
    [OperationContract]  
    Address GetAddress(Person s);  
}  
  
[DataContract]  
public class Person  
{  
    [DataMember]  
    public string firstName;  
    [DataMember]  
    public string lastName;  
    [DataMember]  
    public int age;  
}  
  
[DataContract]  
public class Address  
{  
    [DataMember]  
    public string city;  
    [DataMember]  
    public string state;  
    [DataMember]  
    public string street;  
    [DataMember]  
    public int zipCode;  
    [DataMember]  
    public Person person;  
}  
  
// The following service implementation is compiled into Service.exe.     
// This service uses the contracts specified in Contracts.dll.  
[ServiceBehavior(ConfigurationName = "MyService")]  
public class MyService : IPersonFinder  
{  
    public Address GetAddress(Person person)  
    {  
        Address address = new Address();  
        address.person = person;  
        return address;  
    }  
}  
  
<!-- The following is the configuration file for Service.exe. -->  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="MyService">  
         <endpoint  address="finder"  
                    binding="basicHttpBinding"  
                    contract="IPeopleFinder"/>  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f5f4c-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="f5f4c-130">See Also</span></span>  
 [<span data-ttu-id="f5f4c-131">ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="f5f4c-131">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [<span data-ttu-id="f5f4c-132">メタデータのエクスポートとインポート</span><span class="sxs-lookup"><span data-stu-id="f5f4c-132">Exporting and Importing Metadata</span></span>](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md)
