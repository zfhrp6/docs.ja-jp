---
title: "XmlSerializer によるカスタム シリアル化順序"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 975abd20-2a1d-42db-aed3-e898025ccce7
caps.latest.revision: 9
author: Erikre
ms.author: erikre
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 717bcb6f9f72a728d77e2847096ea558a9c50902
ms.openlocfilehash: fe68a521b8a27f4dd6e5ca9a190a0d37c0ff6410
ms.contentlocale: ja-jp
ms.lasthandoff: 08/21/2017

---
# <a name="custom-serialization-order-with-xmlserializer"></a>XmlSerializer によるカスタム シリアル化順序
[サンプルのダウンロード](http://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Xml%20Serialization/CustomOrder.zip.exe)  
  
 このサンプルでは、XML シリアル化で、シリアル化される要素および逆シリアル化される要素の順序を制御する方法を示します。  
  
 シリアル化の詳細については、ソース コード ファイルおよび build.proj ファイル内のコメントを参照してください。  
  
### <a name="to-build-the-sample-using-the-command-prompt"></a>コマンド プロンプトを使用してサンプルをビルドするには  
  
1.  コマンド プロンプト ウィンドウを開き、サンプルの使用言語に対応するサブディレクトリに移動します。  
  
2.  コマンド ラインで「**msbuild CustomOrder.sln**」と入力します。  
  
### <a name="to-build-the-sample-using-visual-studio"></a>Visual Studio を使用してサンプルをビルドするには  
  
1.  [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)]を開き、サンプルが格納されている、言語固有のサブディレクトリのいずれかに移動します。  
  
2.  CustomOrder.sln のアイコンをダブルクリックして、このファイルを Visual Studio で開きます。  
  
3.  **[ビルド]** メニューの **[ソリューションのビルド]** を選択します。  
  
4.  サンプル アプリケーションは、既定の \bin ディレクトリまたは \bin\Debug ディレクトリにビルドされます。  
  
## <a name="see-also"></a>関連項目  
 [基本的なシリアル化](../../../docs/standard/serialization/basic-serialization.md)   
 [バイナリ シリアル化](../../../docs/standard/serialization/binary-serialization.md)   
 [属性を使用した XML シリアル化の制御](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md)   
 [XML シリアル化の概要](../../../docs/standard/serialization/introducing-xml-serialization.md)   
 [シリアル化](../../../docs/standard/serialization/index.md)   
 [XML シリアル化および SOAP シリアル化](../../../docs/standard/serialization/xml-and-soap-serialization.md)

