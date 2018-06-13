---
title: ConfigurationCodeGenerator
ms.date: 03/30/2017
ms.assetid: 3913aae8-165f-4014-9262-7fe426f90cb2
ms.openlocfilehash: 5575de8a9932777a5bda49a34a108b84593e013c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33500858"
---
# <a name="configurationcodegenerator"></a>ConfigurationCodeGenerator
ConfigurationCodeGenerator は、カスタム チャネルの実装を構成システムに公開する際に使用できるツールです。 カスタム チャネルのユーザーは、このツールを使用することによって、`NetTcpBinding` などのシステム指定のバインディングやカスタム バインディングを `TcpTransportBindingElement` で構成するのと同じように、.config ファイルを使用してカスタム チャネルを構成できます。  
  
 新しい `BindingElement` または `Binding` を使用してカスタム チャネルを記述し、プログラミング モデルに公開する場合は、.config ファイルを使用して、`BindingElement` または `Binding` を構成可能にするためのクラスのセットを作成する必要があります。 ConfigurationCodeGenerator ツールを使用すると、こうしたクラスを生成してユーザーの操作性を向上させることができます。  
  
### <a name="to-build-the-tool"></a>ツールをビルドするには  
  
1.  指示に従って、ソリューションをビルドする[Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)です。  
  
2.  ソリューションをビルドすると、ConfigurationCodeGenerator.exe ファイルが生成されます。 SampleRun.cmd ファイルが、サンプルのコマンド ライン ツールを使用してこのクラスを生成する方法を示しています、[トランスポート: UDP](../../../../docs/framework/wcf/samples/transport-udp.md)サンプルです。  
  
### <a name="to-run-the-tool"></a>ツールを実行するには  
  
1.  `BindingElement` のカスタム型と `Binding` のカスタム型の両方がある場合は、コマンド プロンプトで次のように入力します。  
  
    ```  
    ConfigurationCodeGenerator.exe /be:YourCustomBindingElementTypeName /sb:YourCustomStdBindingTypeName /dll:TheAssemblyWhereTheseTypesAreDefined  
    ```  
  
     `BindingElement` のカスタム型のみがある場合は、次のように入力します。  
  
    ```  
    ConfigurationCodeGenerator.exe /be:YourCustomBindingElementTypeName /dll: TheAssemblyWhereThisTypeIsDefined  
    ```  
  
     `Binding` のカスタム型のみがある場合は、次のように入力します。  
  
    ```  
    ConfigurationCodeGenerator.exe /sb:YourCustomStdBindingTypeName /dll:TheAssemblyWhereThisTypeIsDefined  
    ```  
  
     このコマンドにより、`BindingElement` 用の 3 つの .cs ファイル (/be: オプションを指定した場合)、標準の `Binding` 用の 5 つの .cs ファイル (/sb: オプションを指定した場合)、および 1 つの .xml ファイルが生成されます。  
  
    1.  /be オプションを使用した場合、いずれかの .cs ファイルに、バインディング要素用の `BindingElementExtensionSection` が実装されます。 このコードにより、`BindingElement` が構成システムに公開されます。したがって他のカスタム バインディングも、このバインディング要素を使用できます。 他のファイルには、既定値と定数を示すクラスがあります。 ファイルでは、既定値を更新する必要があることが `//TODO` コメントで示されています。  
  
    2.  /sb オプションを指定した場合、2 つの .cs ファイルにそれぞれ `StandardBindingElement` と `StandardBindingCollectionElement` が実装されます。これによって、標準バインディングが構成システムに公開されます。 他のファイルには、既定値と定数を示すクラスがあります。 ファイルでは、既定値を更新する必要があることが `//TODO` コメントで示されています。  
  
         /Sb を指定した場合: オプション、CodeToAddTo\<*YourStdBinding*> .cs がコードを標準バインディングを実装するクラスに手動で追加する必要があります。  
  
     SampleConfig.xml ファイルには、構成コードが含まれます。このコードは、前の手順 1. または 2. で定義されたハンドラーを登録する構成ファイルに追加する必要があります。  
  
## <a name="see-also"></a>関連項目
