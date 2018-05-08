---
title: WCF ライブラリ プロジェクトの配置
ms.date: 03/30/2017
ms.assetid: 9f9222fe-d358-443c-9a49-12c5498e35e7
ms.openlocfilehash: 08a1d794aeeea1a41cd1eb3abf298f3f4a0f6d15
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="deploying-a-wcf-library-project"></a>WCF ライブラリ プロジェクトの配置
このトピックでは、Windows Communication Foundation (WCF) サービス ライブラリ プロジェクトを配置する方法について説明します。  
  
## <a name="deploying-a-wcf-service-library"></a>WCF サービス ライブラリの配置  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス ライブラリは、ダイナミックリンク ライブラリ (DLL) です。 それ自体を単独で実行することはできません。 ホスティング環境に配置する必要があります。 このプロセスの詳細については、次を参照してください。[ホスティングと WCF サービスの消費](http://go.microsoft.com/fwlink/?LinkId=99932)です。  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス ライブラリは、他の [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービスと同様に配置できます。 ただし、[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] では、DLL に対する構成がサポートされていないことに注意してください。 <xref:System.Configuration> では、アプリケーション ドメイン 1 つにつき、1 つの構成ファイルがサポートされています。 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス ライブラリ プロジェクトにより、配置中、ライブラリに App.config ファイルが提供され、この制限が緩和されます。 ただし、配置後、この App.config ファイルは認識されません。  
  
 構成コードは、ホスティング環境で認識されている構成ファイルに移動する必要があります。 自己ホストを行うには、App.config ファイルの内容をホスティング実行可能形式の App.config ファイルにコピーしてください。 サービスのホスティングに IIS を使用する場合は、App.config ファイルの内容を仮想ディレクトリの Web.config ファイルにコピーする必要があります。
