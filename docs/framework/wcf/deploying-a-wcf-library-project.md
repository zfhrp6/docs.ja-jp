---
title: WCF ライブラリ プロジェクトの配置
ms.date: 03/30/2017
ms.assetid: 9f9222fe-d358-443c-9a49-12c5498e35e7
ms.openlocfilehash: fb400a4d1ebba691222ad7fc9d2c09f1051591da
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
---
# <a name="deploying-a-wcf-library-project"></a>WCF ライブラリ プロジェクトの配置
このトピックでは、Windows Communication Foundation (WCF) サービス ライブラリ プロジェクトを配置する方法について説明します。  
  
## <a name="deploying-a-wcf-service-library"></a>WCF サービス ライブラリの配置  
 WCF サービス ライブラリは、ダイナミック リンク ライブラリ (DLL) です。 それ自体を単独で実行することはできません。 ホスティング環境に配置する必要があります。 このプロセスの詳細については、次を参照してください。[ホスティングと WCF サービスの消費](http://go.microsoft.com/fwlink/?LinkId=99932)です。  
  
 WCF サービス ライブラリは、その他の WCF サービスと同様に展開できます。 ただし、[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] では、DLL に対する構成がサポートされていないことに注意してください。 <xref:System.Configuration> では、アプリケーション ドメイン 1 つにつき、1 つの構成ファイルがサポートされています。 WCF サービス ライブラリ プロジェクトでは、開発時に、ライブラリの App.config ファイルを提供することによってこのような制限が軽減されます。 ただし、配置後、この App.config ファイルは認識されません。  
  
 構成コードは、ホスティング環境で認識されている構成ファイルに移動する必要があります。 自己ホストを行うには、App.config ファイルの内容をホスティング実行可能形式の App.config ファイルにコピーしてください。 サービスのホスティングに IIS を使用する場合は、App.config ファイルの内容を仮想ディレクトリの Web.config ファイルにコピーする必要があります。
