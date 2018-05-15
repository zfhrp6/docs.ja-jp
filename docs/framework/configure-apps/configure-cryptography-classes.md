---
title: 暗号化クラスの設定
ms.date: 03/30/2017
helpviewer_keywords:
- configuration files [.NET Framework], cryptography
- cryptographic algorithms
- security [.NET Framework], encryption
- cryptography, classes
- .NET Framework application configuration, cryptography
- default cryptography
ms.assetid: eee3ccb8-2c0d-4f35-b38d-6892a46c14e5
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: b12d5d95a17439308d79d094e8c22206778f3128
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="configuring-cryptography-classes"></a><span data-ttu-id="6fb96-102">暗号化クラスの設定</span><span class="sxs-lookup"><span data-stu-id="6fb96-102">Configuring Cryptography Classes</span></span>
<span data-ttu-id="6fb96-103">[!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)]により、既定の暗号化アルゴリズムと .NET Framework および適切に記述されたアプリケーションを使用するアルゴリズムの実装を構成するコンピューターの管理者です。</span><span class="sxs-lookup"><span data-stu-id="6fb96-103">The [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] allows computer administrators to configure the default cryptographic algorithms and algorithm implementations that the .NET Framework and appropriately written applications use.</span></span>  <span data-ttu-id="6fb96-104">たとえば、暗号アルゴリズムの実装を持つエンタープライズは、その実装に付属して実装ではなく既定値、[!INCLUDE[winsdkshort](../../../includes/winsdkshort-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="6fb96-104">For example, an enterprise that has its own implementation of a cryptographic algorithm can make that implementation the default instead of the implementation shipped in the [!INCLUDE[winsdkshort](../../../includes/winsdkshort-md.md)].</span></span> <span data-ttu-id="6fb96-105">暗号化を使用するマネージ アプリケーションは、特定の実装にバインドするように常に選択できますが、暗号化の構成システムを使用して暗号オブジェクトを作成することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="6fb96-105">Although managed applications that use cryptography can always choose to explicitly bind to a particular implementation, it is recommended that they create cryptographic objects by using the crypto configuration system.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6fb96-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="6fb96-106">In This Section</span></span>  
 [<span data-ttu-id="6fb96-107">暗号化クラスへのアルゴリズム名の割り当て</span><span class="sxs-lookup"><span data-stu-id="6fb96-107">Mapping Algorithm Names to Cryptography Classes</span></span>](../../../docs/framework/configure-apps/map-algorithm-names-to-cryptography-classes.md)  
 <span data-ttu-id="6fb96-108">アルゴリズム名を暗号クラスにマップする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6fb96-108">Describes how to map an algorithm name to a cryptography class.</span></span>  
  
 [<span data-ttu-id="6fb96-109">暗号化アルゴリズムへのオブジェクト ID の割り当て</span><span class="sxs-lookup"><span data-stu-id="6fb96-109">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../../docs/framework/configure-apps/map-object-identifiers-to-cryptography-algorithms.md)  
 <span data-ttu-id="6fb96-110">暗号化アルゴリズムにオブジェクト識別子をマップする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6fb96-110">Describes how to map an object identifier to a cryptography algorithm.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="6fb96-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="6fb96-111">Related Sections</span></span>  
 [<span data-ttu-id="6fb96-112">Cryptographic Services</span><span class="sxs-lookup"><span data-stu-id="6fb96-112">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)  
 <span data-ttu-id="6fb96-113">によって提供される暗号サービスの概要を示します、[!INCLUDE[winsdkshort](../../../includes/winsdkshort-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="6fb96-113">Provides an overview of cryptographic services provided by the [!INCLUDE[winsdkshort](../../../includes/winsdkshort-md.md)].</span></span>  
  
 [<span data-ttu-id="6fb96-114">暗号化設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="6fb96-114">Cryptography Settings Schema</span></span>](../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 <span data-ttu-id="6fb96-115">アルゴリズムの表示名を、暗号化アルゴリズムを実装するクラスに割り当てる要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="6fb96-115">Describes elements that map friendly algorithm names to classes that implement cryptography algorithms.</span></span>
