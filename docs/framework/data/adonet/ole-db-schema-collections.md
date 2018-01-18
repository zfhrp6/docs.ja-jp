---
title: "OLE DB スキーマ コレクション"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6380c36b-658e-4d67-91e8-7131ef4a7c2c
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 33e794559abd7f619f7431683f06e59705b57d41
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="ole-db-schema-collections"></a><span data-ttu-id="5b3d3-102">OLE DB スキーマ コレクション</span><span class="sxs-lookup"><span data-stu-id="5b3d3-102">OLE DB Schema Collections</span></span>
<span data-ttu-id="5b3d3-103">ここでは、Microsoft SQL Server、Oracle、および Microsoft Jet 用の各 OLE DB プロバイダーでのスキーマ コレクションのサポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="5b3d3-103">This section discusses schema collection support for the OLE DB providers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-ole-db-provider"></a><span data-ttu-id="5b3d3-104">Microsoft SQL Server OLE DB Provider</span><span class="sxs-lookup"><span data-stu-id="5b3d3-104">Microsoft SQL Server OLE DB Provider</span></span>  
 <span data-ttu-id="5b3d3-105">Microsoft SQL Server OLE DB Driver は、共通のスキーマ コレクションに加えて次の特定のスキーマ コレクションをサポートします。</span><span class="sxs-lookup"><span data-stu-id="5b3d3-105">The Microsoft SQL Server OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="5b3d3-106">[テーブル]</span><span class="sxs-lookup"><span data-stu-id="5b3d3-106">Tables</span></span>  
  
-   <span data-ttu-id="5b3d3-107">列</span><span class="sxs-lookup"><span data-stu-id="5b3d3-107">Columns</span></span>  
  
-   <span data-ttu-id="5b3d3-108">手順</span><span class="sxs-lookup"><span data-stu-id="5b3d3-108">Procedures</span></span>  
  
-   <span data-ttu-id="5b3d3-109">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="5b3d3-109">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="5b3d3-110">Catalog</span><span class="sxs-lookup"><span data-stu-id="5b3d3-110">Catalog</span></span>  
  
-   <span data-ttu-id="5b3d3-111">Indexes</span><span class="sxs-lookup"><span data-stu-id="5b3d3-111">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="5b3d3-112">[テーブル]</span><span class="sxs-lookup"><span data-stu-id="5b3d3-112">Tables</span></span>  
  
|<span data-ttu-id="5b3d3-113">ColumnName</span><span class="sxs-lookup"><span data-stu-id="5b3d3-113">ColumnName</span></span>|<span data-ttu-id="5b3d3-114">DataType</span><span class="sxs-lookup"><span data-stu-id="5b3d3-114">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="5b3d3-115">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5b3d3-115">TABLE_CATALOG</span></span>|<span data-ttu-id="5b3d3-116">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-116">String</span></span>|  
|<span data-ttu-id="5b3d3-117">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5b3d3-117">TABLE_SCHEMA</span></span>|<span data-ttu-id="5b3d3-118">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-118">String</span></span>|  
|<span data-ttu-id="5b3d3-119">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="5b3d3-119">TABLE_NAME</span></span>|<span data-ttu-id="5b3d3-120">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-120">String</span></span>|  
|<span data-ttu-id="5b3d3-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="5b3d3-121">TABLE_TYPE</span></span>|<span data-ttu-id="5b3d3-122">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-122">String</span></span>|  
|<span data-ttu-id="5b3d3-123">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="5b3d3-123">TABLE_GUID</span></span>|<span data-ttu-id="5b3d3-124">Guid</span><span class="sxs-lookup"><span data-stu-id="5b3d3-124">Guid</span></span>|  
|<span data-ttu-id="5b3d3-125">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="5b3d3-125">DESCRIPTION</span></span>|<span data-ttu-id="5b3d3-126">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-126">String</span></span>|  
|<span data-ttu-id="5b3d3-127">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="5b3d3-127">TABLE_PROPID</span></span>|<span data-ttu-id="5b3d3-128">Int64</span><span class="sxs-lookup"><span data-stu-id="5b3d3-128">Int64</span></span>|  
|<span data-ttu-id="5b3d3-129">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="5b3d3-129">DATE_CREATED</span></span>|<span data-ttu-id="5b3d3-130">DateTime</span><span class="sxs-lookup"><span data-stu-id="5b3d3-130">DateTime</span></span>|  
|<span data-ttu-id="5b3d3-131">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="5b3d3-131">DATE_MODIFIED</span></span>|<span data-ttu-id="5b3d3-132">DateTime</span><span class="sxs-lookup"><span data-stu-id="5b3d3-132">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="5b3d3-133">列</span><span class="sxs-lookup"><span data-stu-id="5b3d3-133">Columns</span></span>  
  
|<span data-ttu-id="5b3d3-134">ColumnName</span><span class="sxs-lookup"><span data-stu-id="5b3d3-134">ColumnName</span></span>|<span data-ttu-id="5b3d3-135">DataType</span><span class="sxs-lookup"><span data-stu-id="5b3d3-135">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="5b3d3-136">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5b3d3-136">TABLE_CATALOG</span></span>|<span data-ttu-id="5b3d3-137">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-137">String</span></span>|  
|<span data-ttu-id="5b3d3-138">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5b3d3-138">TABLE_SCHEMA</span></span>|<span data-ttu-id="5b3d3-139">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-139">String</span></span>|  
|<span data-ttu-id="5b3d3-140">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="5b3d3-140">TABLE_NAME</span></span>|<span data-ttu-id="5b3d3-141">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-141">String</span></span>|  
|<span data-ttu-id="5b3d3-142">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="5b3d3-142">COLUMN_NAME</span></span>|<span data-ttu-id="5b3d3-143">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-143">String</span></span>|  
|<span data-ttu-id="5b3d3-144">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="5b3d3-144">COLUMN_GUID</span></span>|<span data-ttu-id="5b3d3-145">Guid</span><span class="sxs-lookup"><span data-stu-id="5b3d3-145">Guid</span></span>|  
|<span data-ttu-id="5b3d3-146">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="5b3d3-146">COLUMN_PROPID</span></span>|<span data-ttu-id="5b3d3-147">Int64</span><span class="sxs-lookup"><span data-stu-id="5b3d3-147">Int64</span></span>|  
|<span data-ttu-id="5b3d3-148">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="5b3d3-148">ORDINAL_POSITION</span></span>|<span data-ttu-id="5b3d3-149">Int64</span><span class="sxs-lookup"><span data-stu-id="5b3d3-149">Int64</span></span>|  
|<span data-ttu-id="5b3d3-150">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="5b3d3-150">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="5b3d3-151">Boolean</span><span class="sxs-lookup"><span data-stu-id="5b3d3-151">Boolean</span></span>|  
|<span data-ttu-id="5b3d3-152">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="5b3d3-152">COLUMN_DEFAULT</span></span>|<span data-ttu-id="5b3d3-153">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-153">String</span></span>|  
|<span data-ttu-id="5b3d3-154">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="5b3d3-154">COLUMN_FLAGS</span></span>|<span data-ttu-id="5b3d3-155">Int64</span><span class="sxs-lookup"><span data-stu-id="5b3d3-155">Int64</span></span>|  
|<span data-ttu-id="5b3d3-156">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="5b3d3-156">IS_NULLABLE</span></span>|<span data-ttu-id="5b3d3-157">Boolean</span><span class="sxs-lookup"><span data-stu-id="5b3d3-157">Boolean</span></span>|  
|<span data-ttu-id="5b3d3-158">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="5b3d3-158">DATA_TYPE</span></span>|<span data-ttu-id="5b3d3-159">Int32</span><span class="sxs-lookup"><span data-stu-id="5b3d3-159">Int32</span></span>|  
|<span data-ttu-id="5b3d3-160">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="5b3d3-160">TYPE_GUID</span></span>|<span data-ttu-id="5b3d3-161">Guid</span><span class="sxs-lookup"><span data-stu-id="5b3d3-161">Guid</span></span>|  
|<span data-ttu-id="5b3d3-162">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="5b3d3-162">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="5b3d3-163">Int64</span><span class="sxs-lookup"><span data-stu-id="5b3d3-163">Int64</span></span>|  
|<span data-ttu-id="5b3d3-164">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="5b3d3-164">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="5b3d3-165">Int64</span><span class="sxs-lookup"><span data-stu-id="5b3d3-165">Int64</span></span>|  
|<span data-ttu-id="5b3d3-166">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="5b3d3-166">NUMERIC_PRECISION</span></span>|<span data-ttu-id="5b3d3-167">Int32</span><span class="sxs-lookup"><span data-stu-id="5b3d3-167">Int32</span></span>|  
|<span data-ttu-id="5b3d3-168">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="5b3d3-168">NUMERIC_SCALE</span></span>|<span data-ttu-id="5b3d3-169">Int16</span><span class="sxs-lookup"><span data-stu-id="5b3d3-169">Int16</span></span>|  
|<span data-ttu-id="5b3d3-170">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="5b3d3-170">DATETIME_PRECISION</span></span>|<span data-ttu-id="5b3d3-171">Int64</span><span class="sxs-lookup"><span data-stu-id="5b3d3-171">Int64</span></span>|  
|<span data-ttu-id="5b3d3-172">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5b3d3-172">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="5b3d3-173">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-173">String</span></span>|  
|<span data-ttu-id="5b3d3-174">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5b3d3-174">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="5b3d3-175">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-175">String</span></span>|  
|<span data-ttu-id="5b3d3-176">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="5b3d3-176">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="5b3d3-177">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-177">String</span></span>|  
|<span data-ttu-id="5b3d3-178">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5b3d3-178">COLLATION_CATALOG</span></span>|<span data-ttu-id="5b3d3-179">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-179">String</span></span>|  
|<span data-ttu-id="5b3d3-180">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5b3d3-180">COLLATION_SCHEMA</span></span>|<span data-ttu-id="5b3d3-181">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-181">String</span></span>|  
|<span data-ttu-id="5b3d3-182">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="5b3d3-182">COLLATION_NAME</span></span>|<span data-ttu-id="5b3d3-183">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-183">String</span></span>|  
|<span data-ttu-id="5b3d3-184">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5b3d3-184">DOMAIN_CATALOG</span></span>|<span data-ttu-id="5b3d3-185">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-185">String</span></span>|  
|<span data-ttu-id="5b3d3-186">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5b3d3-186">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="5b3d3-187">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-187">String</span></span>|  
|<span data-ttu-id="5b3d3-188">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="5b3d3-188">DOMAIN_NAME</span></span>|<span data-ttu-id="5b3d3-189">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-189">String</span></span>|  
|<span data-ttu-id="5b3d3-190">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="5b3d3-190">DESCRIPTION</span></span>|<span data-ttu-id="5b3d3-191">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-191">String</span></span>|  
|<span data-ttu-id="5b3d3-192">COLUMN_LCID</span><span class="sxs-lookup"><span data-stu-id="5b3d3-192">COLUMN_LCID</span></span>|<span data-ttu-id="5b3d3-193">Int32</span><span class="sxs-lookup"><span data-stu-id="5b3d3-193">Int32</span></span>|  
|<span data-ttu-id="5b3d3-194">COLUMN_COMPFLAGS</span><span class="sxs-lookup"><span data-stu-id="5b3d3-194">COLUMN_COMPFLAGS</span></span>|<span data-ttu-id="5b3d3-195">Int32</span><span class="sxs-lookup"><span data-stu-id="5b3d3-195">Int32</span></span>|  
|<span data-ttu-id="5b3d3-196">COLUMN_SORTID</span><span class="sxs-lookup"><span data-stu-id="5b3d3-196">COLUMN_SORTID</span></span>|<span data-ttu-id="5b3d3-197">Int32</span><span class="sxs-lookup"><span data-stu-id="5b3d3-197">Int32</span></span>|  
|<span data-ttu-id="5b3d3-198">COLUMN_TDSCOLLATION</span><span class="sxs-lookup"><span data-stu-id="5b3d3-198">COLUMN_TDSCOLLATION</span></span>|<span data-ttu-id="5b3d3-199">Byte[]</span><span class="sxs-lookup"><span data-stu-id="5b3d3-199">Byte[]</span></span>|  
|<span data-ttu-id="5b3d3-200">IS_COMPUTED</span><span class="sxs-lookup"><span data-stu-id="5b3d3-200">IS_COMPUTED</span></span>|<span data-ttu-id="5b3d3-201">Boolean</span><span class="sxs-lookup"><span data-stu-id="5b3d3-201">Boolean</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="5b3d3-202">手順</span><span class="sxs-lookup"><span data-stu-id="5b3d3-202">Procedures</span></span>  
  
|<span data-ttu-id="5b3d3-203">ColumnName</span><span class="sxs-lookup"><span data-stu-id="5b3d3-203">ColumnName</span></span>|<span data-ttu-id="5b3d3-204">DataType</span><span class="sxs-lookup"><span data-stu-id="5b3d3-204">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="5b3d3-205">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5b3d3-205">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="5b3d3-206">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-206">String</span></span>|  
|<span data-ttu-id="5b3d3-207">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5b3d3-207">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="5b3d3-208">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-208">String</span></span>|  
|<span data-ttu-id="5b3d3-209">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="5b3d3-209">PROCEDURE_NAME</span></span>|<span data-ttu-id="5b3d3-210">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-210">String</span></span>|  
|<span data-ttu-id="5b3d3-211">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="5b3d3-211">PROCEDURE_TYPE</span></span>|<span data-ttu-id="5b3d3-212">Int16</span><span class="sxs-lookup"><span data-stu-id="5b3d3-212">Int16</span></span>|  
|<span data-ttu-id="5b3d3-213">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="5b3d3-213">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="5b3d3-214">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-214">String</span></span>|  
|<span data-ttu-id="5b3d3-215">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="5b3d3-215">DESCRIPTION</span></span>|<span data-ttu-id="5b3d3-216">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-216">String</span></span>|  
|<span data-ttu-id="5b3d3-217">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="5b3d3-217">DATE_CREATED</span></span>|<span data-ttu-id="5b3d3-218">DateTime</span><span class="sxs-lookup"><span data-stu-id="5b3d3-218">DateTime</span></span>|  
|<span data-ttu-id="5b3d3-219">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="5b3d3-219">DATE_MODIFIED</span></span>|<span data-ttu-id="5b3d3-220">DateTime</span><span class="sxs-lookup"><span data-stu-id="5b3d3-220">DateTime</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="5b3d3-221">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="5b3d3-221">ProcedureParameters</span></span>  
  
|<span data-ttu-id="5b3d3-222">ColumnName</span><span class="sxs-lookup"><span data-stu-id="5b3d3-222">ColumnName</span></span>|<span data-ttu-id="5b3d3-223">DataType</span><span class="sxs-lookup"><span data-stu-id="5b3d3-223">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="5b3d3-224">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5b3d3-224">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="5b3d3-225">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-225">String</span></span>|  
|<span data-ttu-id="5b3d3-226">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5b3d3-226">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="5b3d3-227">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-227">String</span></span>|  
|<span data-ttu-id="5b3d3-228">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="5b3d3-228">PROCEDURE_NAME</span></span>|<span data-ttu-id="5b3d3-229">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-229">String</span></span>|  
|<span data-ttu-id="5b3d3-230">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="5b3d3-230">PARAMETER_NAME</span></span>|<span data-ttu-id="5b3d3-231">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-231">String</span></span>|  
|<span data-ttu-id="5b3d3-232">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="5b3d3-232">ORDINAL_POSITION</span></span>|<span data-ttu-id="5b3d3-233">Int32</span><span class="sxs-lookup"><span data-stu-id="5b3d3-233">Int32</span></span>|  
|<span data-ttu-id="5b3d3-234">PARAMETER_TYPE</span><span class="sxs-lookup"><span data-stu-id="5b3d3-234">PARAMETER_TYPE</span></span>|<span data-ttu-id="5b3d3-235">Int32</span><span class="sxs-lookup"><span data-stu-id="5b3d3-235">Int32</span></span>|  
|<span data-ttu-id="5b3d3-236">PARAMETER_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="5b3d3-236">PARAMETER_HASDEFAULT</span></span>|<span data-ttu-id="5b3d3-237">Boolean</span><span class="sxs-lookup"><span data-stu-id="5b3d3-237">Boolean</span></span>|  
|<span data-ttu-id="5b3d3-238">PARAMETER_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="5b3d3-238">PARAMETER_DEFAULT</span></span>|<span data-ttu-id="5b3d3-239">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-239">String</span></span>|  
|<span data-ttu-id="5b3d3-240">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="5b3d3-240">IS_NULLABLE</span></span>|<span data-ttu-id="5b3d3-241">Boolean</span><span class="sxs-lookup"><span data-stu-id="5b3d3-241">Boolean</span></span>|  
|<span data-ttu-id="5b3d3-242">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="5b3d3-242">DATA_TYPE</span></span>|<span data-ttu-id="5b3d3-243">Int32</span><span class="sxs-lookup"><span data-stu-id="5b3d3-243">Int32</span></span>|  
|<span data-ttu-id="5b3d3-244">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="5b3d3-244">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="5b3d3-245">Int64</span><span class="sxs-lookup"><span data-stu-id="5b3d3-245">Int64</span></span>|  
|<span data-ttu-id="5b3d3-246">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="5b3d3-246">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="5b3d3-247">Int64</span><span class="sxs-lookup"><span data-stu-id="5b3d3-247">Int64</span></span>|  
|<span data-ttu-id="5b3d3-248">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="5b3d3-248">NUMERIC_PRECISION</span></span>|<span data-ttu-id="5b3d3-249">Int32</span><span class="sxs-lookup"><span data-stu-id="5b3d3-249">Int32</span></span>|  
|<span data-ttu-id="5b3d3-250">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="5b3d3-250">NUMERIC_SCALE</span></span>|<span data-ttu-id="5b3d3-251">Int16</span><span class="sxs-lookup"><span data-stu-id="5b3d3-251">Int16</span></span>|  
|<span data-ttu-id="5b3d3-252">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="5b3d3-252">DESCRIPTION</span></span>|<span data-ttu-id="5b3d3-253">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-253">String</span></span>|  
|<span data-ttu-id="5b3d3-254">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="5b3d3-254">TYPE_NAME</span></span>|<span data-ttu-id="5b3d3-255">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-255">String</span></span>|  
|<span data-ttu-id="5b3d3-256">LOCAL_TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="5b3d3-256">LOCAL_TYPE_NAME</span></span>|<span data-ttu-id="5b3d3-257">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-257">String</span></span>|  
  
### <a name="catalog"></a><span data-ttu-id="5b3d3-258">Catalog</span><span class="sxs-lookup"><span data-stu-id="5b3d3-258">Catalog</span></span>  
  
|<span data-ttu-id="5b3d3-259">ColumnName</span><span class="sxs-lookup"><span data-stu-id="5b3d3-259">ColumnName</span></span>|<span data-ttu-id="5b3d3-260">DataType</span><span class="sxs-lookup"><span data-stu-id="5b3d3-260">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="5b3d3-261">CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="5b3d3-261">CATALOG_NAME</span></span>|<span data-ttu-id="5b3d3-262">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-262">String</span></span>|  
|<span data-ttu-id="5b3d3-263">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="5b3d3-263">DESCRIPTION</span></span>|<span data-ttu-id="5b3d3-264">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-264">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="5b3d3-265">Indexes</span><span class="sxs-lookup"><span data-stu-id="5b3d3-265">Indexes</span></span>  
  
|<span data-ttu-id="5b3d3-266">ColumnName</span><span class="sxs-lookup"><span data-stu-id="5b3d3-266">ColumnName</span></span>|<span data-ttu-id="5b3d3-267">DataType</span><span class="sxs-lookup"><span data-stu-id="5b3d3-267">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="5b3d3-268">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5b3d3-268">TABLE_CATALOG</span></span>|<span data-ttu-id="5b3d3-269">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-269">String</span></span>|  
|<span data-ttu-id="5b3d3-270">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5b3d3-270">TABLE_SCHEMA</span></span>|<span data-ttu-id="5b3d3-271">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-271">String</span></span>|  
|<span data-ttu-id="5b3d3-272">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="5b3d3-272">TABLE_NAME</span></span>|<span data-ttu-id="5b3d3-273">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-273">String</span></span>|  
|<span data-ttu-id="5b3d3-274">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5b3d3-274">INDEX_CATALOG</span></span>|<span data-ttu-id="5b3d3-275">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-275">String</span></span>|  
|<span data-ttu-id="5b3d3-276">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5b3d3-276">INDEX_SCHEMA</span></span>|<span data-ttu-id="5b3d3-277">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-277">String</span></span>|  
|<span data-ttu-id="5b3d3-278">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="5b3d3-278">INDEX_NAME</span></span>|<span data-ttu-id="5b3d3-279">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-279">String</span></span>|  
|<span data-ttu-id="5b3d3-280">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="5b3d3-280">PRIMARY_KEY</span></span>|<span data-ttu-id="5b3d3-281">Boolean</span><span class="sxs-lookup"><span data-stu-id="5b3d3-281">Boolean</span></span>|  
|<span data-ttu-id="5b3d3-282">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="5b3d3-282">UNIQUE</span></span>|<span data-ttu-id="5b3d3-283">Boolean</span><span class="sxs-lookup"><span data-stu-id="5b3d3-283">Boolean</span></span>|  
|<span data-ttu-id="5b3d3-284">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="5b3d3-284">CLUSTERED</span></span>|<span data-ttu-id="5b3d3-285">Boolean</span><span class="sxs-lookup"><span data-stu-id="5b3d3-285">Boolean</span></span>|  
|<span data-ttu-id="5b3d3-286">TYPE</span><span class="sxs-lookup"><span data-stu-id="5b3d3-286">TYPE</span></span>|<span data-ttu-id="5b3d3-287">Int32</span><span class="sxs-lookup"><span data-stu-id="5b3d3-287">Int32</span></span>|  
|<span data-ttu-id="5b3d3-288">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="5b3d3-288">FILL_FACTOR</span></span>|<span data-ttu-id="5b3d3-289">Int32</span><span class="sxs-lookup"><span data-stu-id="5b3d3-289">Int32</span></span>|  
|<span data-ttu-id="5b3d3-290">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="5b3d3-290">INITIAL_SIZE</span></span>|<span data-ttu-id="5b3d3-291">Int32</span><span class="sxs-lookup"><span data-stu-id="5b3d3-291">Int32</span></span>|  
|<span data-ttu-id="5b3d3-292">NULLS</span><span class="sxs-lookup"><span data-stu-id="5b3d3-292">NULLS</span></span>|<span data-ttu-id="5b3d3-293">Int32</span><span class="sxs-lookup"><span data-stu-id="5b3d3-293">Int32</span></span>|  
|<span data-ttu-id="5b3d3-294">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="5b3d3-294">SORT_BOOKMARKS</span></span>|<span data-ttu-id="5b3d3-295">Boolean</span><span class="sxs-lookup"><span data-stu-id="5b3d3-295">Boolean</span></span>|  
|<span data-ttu-id="5b3d3-296">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="5b3d3-296">AUTO_UPDATE</span></span>|<span data-ttu-id="5b3d3-297">Boolean</span><span class="sxs-lookup"><span data-stu-id="5b3d3-297">Boolean</span></span>|  
|<span data-ttu-id="5b3d3-298">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="5b3d3-298">NULL_COLLATION</span></span>|<span data-ttu-id="5b3d3-299">Int32</span><span class="sxs-lookup"><span data-stu-id="5b3d3-299">Int32</span></span>|  
|<span data-ttu-id="5b3d3-300">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="5b3d3-300">ORDINAL_POSITION</span></span>|<span data-ttu-id="5b3d3-301">Int64</span><span class="sxs-lookup"><span data-stu-id="5b3d3-301">Int64</span></span>|  
|<span data-ttu-id="5b3d3-302">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="5b3d3-302">COLUMN_NAME</span></span>|<span data-ttu-id="5b3d3-303">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-303">String</span></span>|  
|<span data-ttu-id="5b3d3-304">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="5b3d3-304">COLUMN_GUID</span></span>|<span data-ttu-id="5b3d3-305">Guid</span><span class="sxs-lookup"><span data-stu-id="5b3d3-305">Guid</span></span>|  
|<span data-ttu-id="5b3d3-306">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="5b3d3-306">COLUMN_PROPID</span></span>|<span data-ttu-id="5b3d3-307">Int64</span><span class="sxs-lookup"><span data-stu-id="5b3d3-307">Int64</span></span>|  
|<span data-ttu-id="5b3d3-308">COLLATION</span><span class="sxs-lookup"><span data-stu-id="5b3d3-308">COLLATION</span></span>|<span data-ttu-id="5b3d3-309">Int16</span><span class="sxs-lookup"><span data-stu-id="5b3d3-309">Int16</span></span>|  
|<span data-ttu-id="5b3d3-310">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="5b3d3-310">CARDINALITY</span></span>|<span data-ttu-id="5b3d3-311">Decimal (10 進数型)</span><span class="sxs-lookup"><span data-stu-id="5b3d3-311">Decimal</span></span>|  
|<span data-ttu-id="5b3d3-312">PAGES</span><span class="sxs-lookup"><span data-stu-id="5b3d3-312">PAGES</span></span>|<span data-ttu-id="5b3d3-313">Int32</span><span class="sxs-lookup"><span data-stu-id="5b3d3-313">Int32</span></span>|  
|<span data-ttu-id="5b3d3-314">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="5b3d3-314">FILTER_CONDITION</span></span>|<span data-ttu-id="5b3d3-315">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-315">String</span></span>|  
|<span data-ttu-id="5b3d3-316">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="5b3d3-316">INTEGRATED</span></span>|<span data-ttu-id="5b3d3-317">Boolean</span><span class="sxs-lookup"><span data-stu-id="5b3d3-317">Boolean</span></span>|  
  
## <a name="microsoft-oracle-ole-db-provider"></a><span data-ttu-id="5b3d3-318">Microsoft Oracle OLE DB Provider</span><span class="sxs-lookup"><span data-stu-id="5b3d3-318">Microsoft Oracle OLE DB Provider</span></span>  
 <span data-ttu-id="5b3d3-319">Microsoft Oracle OLE DB Driver は、共通のスキーマ コレクションに加えて次のスキーマ コレクションをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="5b3d3-319">The Microsoft Oracle OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="5b3d3-320">[テーブル]</span><span class="sxs-lookup"><span data-stu-id="5b3d3-320">Tables</span></span>  
  
-   <span data-ttu-id="5b3d3-321">列</span><span class="sxs-lookup"><span data-stu-id="5b3d3-321">Columns</span></span>  
  
-   <span data-ttu-id="5b3d3-322">手順</span><span class="sxs-lookup"><span data-stu-id="5b3d3-322">Procedures</span></span>  
  
-   <span data-ttu-id="5b3d3-323">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="5b3d3-323">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="5b3d3-324">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="5b3d3-324">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="5b3d3-325">ビュー</span><span class="sxs-lookup"><span data-stu-id="5b3d3-325">Views</span></span>  
  
-   <span data-ttu-id="5b3d3-326">Indexes</span><span class="sxs-lookup"><span data-stu-id="5b3d3-326">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="5b3d3-327">[テーブル]</span><span class="sxs-lookup"><span data-stu-id="5b3d3-327">Tables</span></span>  
  
|<span data-ttu-id="5b3d3-328">ColumnName</span><span class="sxs-lookup"><span data-stu-id="5b3d3-328">ColumnName</span></span>|<span data-ttu-id="5b3d3-329">DataType</span><span class="sxs-lookup"><span data-stu-id="5b3d3-329">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="5b3d3-330">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5b3d3-330">TABLE_CATALOG</span></span>|<span data-ttu-id="5b3d3-331">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-331">String</span></span>|  
|<span data-ttu-id="5b3d3-332">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5b3d3-332">TABLE_SCHEMA</span></span>|<span data-ttu-id="5b3d3-333">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-333">String</span></span>|  
|<span data-ttu-id="5b3d3-334">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="5b3d3-334">TABLE_NAME</span></span>|<span data-ttu-id="5b3d3-335">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-335">String</span></span>|  
|<span data-ttu-id="5b3d3-336">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="5b3d3-336">TABLE_TYPE</span></span>|<span data-ttu-id="5b3d3-337">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-337">String</span></span>|  
|<span data-ttu-id="5b3d3-338">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="5b3d3-338">TABLE_GUID</span></span>|<span data-ttu-id="5b3d3-339">Guid</span><span class="sxs-lookup"><span data-stu-id="5b3d3-339">Guid</span></span>|  
|<span data-ttu-id="5b3d3-340">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="5b3d3-340">DESCRIPTION</span></span>|<span data-ttu-id="5b3d3-341">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-341">String</span></span>|  
|<span data-ttu-id="5b3d3-342">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="5b3d3-342">TABLE_PROPID</span></span>|<span data-ttu-id="5b3d3-343">Int64</span><span class="sxs-lookup"><span data-stu-id="5b3d3-343">Int64</span></span>|  
|<span data-ttu-id="5b3d3-344">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="5b3d3-344">DATE_CREATED</span></span>|<span data-ttu-id="5b3d3-345">DateTime</span><span class="sxs-lookup"><span data-stu-id="5b3d3-345">DateTime</span></span>|  
|<span data-ttu-id="5b3d3-346">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="5b3d3-346">DATE_MODIFIED</span></span>|<span data-ttu-id="5b3d3-347">DateTime</span><span class="sxs-lookup"><span data-stu-id="5b3d3-347">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="5b3d3-348">列</span><span class="sxs-lookup"><span data-stu-id="5b3d3-348">Columns</span></span>  
  
|<span data-ttu-id="5b3d3-349">ColumnName</span><span class="sxs-lookup"><span data-stu-id="5b3d3-349">ColumnName</span></span>|<span data-ttu-id="5b3d3-350">DataType</span><span class="sxs-lookup"><span data-stu-id="5b3d3-350">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="5b3d3-351">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5b3d3-351">TABLE_CATALOG</span></span>|<span data-ttu-id="5b3d3-352">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-352">String</span></span>|  
|<span data-ttu-id="5b3d3-353">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5b3d3-353">TABLE_SCHEMA</span></span>|<span data-ttu-id="5b3d3-354">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-354">String</span></span>|  
|<span data-ttu-id="5b3d3-355">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="5b3d3-355">TABLE_NAME</span></span>|<span data-ttu-id="5b3d3-356">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-356">String</span></span>|  
|<span data-ttu-id="5b3d3-357">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="5b3d3-357">COLUMN_NAME</span></span>|<span data-ttu-id="5b3d3-358">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-358">String</span></span>|  
|<span data-ttu-id="5b3d3-359">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="5b3d3-359">COLUMN_GUID</span></span>|<span data-ttu-id="5b3d3-360">Guid</span><span class="sxs-lookup"><span data-stu-id="5b3d3-360">Guid</span></span>|  
|<span data-ttu-id="5b3d3-361">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="5b3d3-361">COLUMN_PROPID</span></span>|<span data-ttu-id="5b3d3-362">Int64</span><span class="sxs-lookup"><span data-stu-id="5b3d3-362">Int64</span></span>|  
|<span data-ttu-id="5b3d3-363">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="5b3d3-363">ORDINAL_POSITION</span></span>|<span data-ttu-id="5b3d3-364">Int64</span><span class="sxs-lookup"><span data-stu-id="5b3d3-364">Int64</span></span>|  
|<span data-ttu-id="5b3d3-365">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="5b3d3-365">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="5b3d3-366">Boolean</span><span class="sxs-lookup"><span data-stu-id="5b3d3-366">Boolean</span></span>|  
|<span data-ttu-id="5b3d3-367">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="5b3d3-367">COLUMN_DEFAULT</span></span>|<span data-ttu-id="5b3d3-368">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-368">String</span></span>|  
|<span data-ttu-id="5b3d3-369">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="5b3d3-369">COLUMN_FLAGS</span></span>|<span data-ttu-id="5b3d3-370">Int64</span><span class="sxs-lookup"><span data-stu-id="5b3d3-370">Int64</span></span>|  
|<span data-ttu-id="5b3d3-371">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="5b3d3-371">IS_NULLABLE</span></span>|<span data-ttu-id="5b3d3-372">Boolean</span><span class="sxs-lookup"><span data-stu-id="5b3d3-372">Boolean</span></span>|  
|<span data-ttu-id="5b3d3-373">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="5b3d3-373">DATA_TYPE</span></span>|<span data-ttu-id="5b3d3-374">Int32</span><span class="sxs-lookup"><span data-stu-id="5b3d3-374">Int32</span></span>|  
|<span data-ttu-id="5b3d3-375">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="5b3d3-375">TYPE_GUID</span></span>|<span data-ttu-id="5b3d3-376">Guid</span><span class="sxs-lookup"><span data-stu-id="5b3d3-376">Guid</span></span>|  
|<span data-ttu-id="5b3d3-377">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="5b3d3-377">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="5b3d3-378">Int64</span><span class="sxs-lookup"><span data-stu-id="5b3d3-378">Int64</span></span>|  
|<span data-ttu-id="5b3d3-379">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="5b3d3-379">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="5b3d3-380">Int64</span><span class="sxs-lookup"><span data-stu-id="5b3d3-380">Int64</span></span>|  
|<span data-ttu-id="5b3d3-381">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="5b3d3-381">NUMERIC_PRECISION</span></span>|<span data-ttu-id="5b3d3-382">Int32</span><span class="sxs-lookup"><span data-stu-id="5b3d3-382">Int32</span></span>|  
|<span data-ttu-id="5b3d3-383">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="5b3d3-383">NUMERIC_SCALE</span></span>|<span data-ttu-id="5b3d3-384">Int16</span><span class="sxs-lookup"><span data-stu-id="5b3d3-384">Int16</span></span>|  
|<span data-ttu-id="5b3d3-385">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="5b3d3-385">DATETIME_PRECISION</span></span>|<span data-ttu-id="5b3d3-386">Int64</span><span class="sxs-lookup"><span data-stu-id="5b3d3-386">Int64</span></span>|  
|<span data-ttu-id="5b3d3-387">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5b3d3-387">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="5b3d3-388">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-388">String</span></span>|  
|<span data-ttu-id="5b3d3-389">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5b3d3-389">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="5b3d3-390">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-390">String</span></span>|  
|<span data-ttu-id="5b3d3-391">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="5b3d3-391">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="5b3d3-392">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-392">String</span></span>|  
|<span data-ttu-id="5b3d3-393">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5b3d3-393">COLLATION_CATALOG</span></span>|<span data-ttu-id="5b3d3-394">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-394">String</span></span>|  
|<span data-ttu-id="5b3d3-395">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5b3d3-395">COLLATION_SCHEMA</span></span>|<span data-ttu-id="5b3d3-396">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-396">String</span></span>|  
|<span data-ttu-id="5b3d3-397">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="5b3d3-397">COLLATION_NAME</span></span>|<span data-ttu-id="5b3d3-398">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-398">String</span></span>|  
|<span data-ttu-id="5b3d3-399">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5b3d3-399">DOMAIN_CATALOG</span></span>|<span data-ttu-id="5b3d3-400">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-400">String</span></span>|  
|<span data-ttu-id="5b3d3-401">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5b3d3-401">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="5b3d3-402">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-402">String</span></span>|  
|<span data-ttu-id="5b3d3-403">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="5b3d3-403">DOMAIN_NAME</span></span>|<span data-ttu-id="5b3d3-404">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-404">String</span></span>|  
|<span data-ttu-id="5b3d3-405">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="5b3d3-405">DESCRIPTION</span></span>|<span data-ttu-id="5b3d3-406">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-406">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="5b3d3-407">手順</span><span class="sxs-lookup"><span data-stu-id="5b3d3-407">Procedures</span></span>  
  
|<span data-ttu-id="5b3d3-408">ColumnName</span><span class="sxs-lookup"><span data-stu-id="5b3d3-408">ColumnName</span></span>|<span data-ttu-id="5b3d3-409">DataType</span><span class="sxs-lookup"><span data-stu-id="5b3d3-409">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="5b3d3-410">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5b3d3-410">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="5b3d3-411">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-411">String</span></span>|  
|<span data-ttu-id="5b3d3-412">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5b3d3-412">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="5b3d3-413">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-413">String</span></span>|  
|<span data-ttu-id="5b3d3-414">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="5b3d3-414">PROCEDURE_NAME</span></span>|<span data-ttu-id="5b3d3-415">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-415">String</span></span>|  
|<span data-ttu-id="5b3d3-416">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="5b3d3-416">PROCEDURE_TYPE</span></span>|<span data-ttu-id="5b3d3-417">Int16</span><span class="sxs-lookup"><span data-stu-id="5b3d3-417">Int16</span></span>|  
|<span data-ttu-id="5b3d3-418">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="5b3d3-418">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="5b3d3-419">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-419">String</span></span>|  
|<span data-ttu-id="5b3d3-420">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="5b3d3-420">DESCRIPTION</span></span>|<span data-ttu-id="5b3d3-421">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-421">String</span></span>|  
|<span data-ttu-id="5b3d3-422">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="5b3d3-422">DATE_CREATED</span></span>|<span data-ttu-id="5b3d3-423">DateTime</span><span class="sxs-lookup"><span data-stu-id="5b3d3-423">DateTime</span></span>|  
|<span data-ttu-id="5b3d3-424">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="5b3d3-424">DATE_MODIFIED</span></span>|<span data-ttu-id="5b3d3-425">DateTime</span><span class="sxs-lookup"><span data-stu-id="5b3d3-425">DateTime</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="5b3d3-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="5b3d3-426">ProcedureColumns</span></span>  
  
|<span data-ttu-id="5b3d3-427">ColumnName</span><span class="sxs-lookup"><span data-stu-id="5b3d3-427">ColumnName</span></span>|<span data-ttu-id="5b3d3-428">DataType</span><span class="sxs-lookup"><span data-stu-id="5b3d3-428">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="5b3d3-429">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5b3d3-429">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="5b3d3-430">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-430">String</span></span>|  
|<span data-ttu-id="5b3d3-431">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5b3d3-431">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="5b3d3-432">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-432">String</span></span>|  
|<span data-ttu-id="5b3d3-433">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="5b3d3-433">PROCEDURE_NAME</span></span>|<span data-ttu-id="5b3d3-434">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-434">String</span></span>|  
|<span data-ttu-id="5b3d3-435">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="5b3d3-435">COLUMN_NAME</span></span>|<span data-ttu-id="5b3d3-436">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-436">String</span></span>|  
|<span data-ttu-id="5b3d3-437">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="5b3d3-437">COLUMN_GUID</span></span>|<span data-ttu-id="5b3d3-438">Guid</span><span class="sxs-lookup"><span data-stu-id="5b3d3-438">Guid</span></span>|  
|<span data-ttu-id="5b3d3-439">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="5b3d3-439">COLUMN_PROPID</span></span>|<span data-ttu-id="5b3d3-440">Int64</span><span class="sxs-lookup"><span data-stu-id="5b3d3-440">Int64</span></span>|  
|<span data-ttu-id="5b3d3-441">ROWSET_NUMBER</span><span class="sxs-lookup"><span data-stu-id="5b3d3-441">ROWSET_NUMBER</span></span>|<span data-ttu-id="5b3d3-442">Int64</span><span class="sxs-lookup"><span data-stu-id="5b3d3-442">Int64</span></span>|  
|<span data-ttu-id="5b3d3-443">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="5b3d3-443">ORDINAL_POSITION</span></span>|<span data-ttu-id="5b3d3-444">Int64</span><span class="sxs-lookup"><span data-stu-id="5b3d3-444">Int64</span></span>|  
|<span data-ttu-id="5b3d3-445">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="5b3d3-445">IS_NULLABLE</span></span>|<span data-ttu-id="5b3d3-446">Boolean</span><span class="sxs-lookup"><span data-stu-id="5b3d3-446">Boolean</span></span>|  
|<span data-ttu-id="5b3d3-447">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="5b3d3-447">DATA_TYPE</span></span>|<span data-ttu-id="5b3d3-448">Int32</span><span class="sxs-lookup"><span data-stu-id="5b3d3-448">Int32</span></span>|  
|<span data-ttu-id="5b3d3-449">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="5b3d3-449">TYPE_GUID</span></span>|<span data-ttu-id="5b3d3-450">Guid</span><span class="sxs-lookup"><span data-stu-id="5b3d3-450">Guid</span></span>|  
|<span data-ttu-id="5b3d3-451">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="5b3d3-451">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="5b3d3-452">Int64</span><span class="sxs-lookup"><span data-stu-id="5b3d3-452">Int64</span></span>|  
|<span data-ttu-id="5b3d3-453">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="5b3d3-453">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="5b3d3-454">Int64</span><span class="sxs-lookup"><span data-stu-id="5b3d3-454">Int64</span></span>|  
|<span data-ttu-id="5b3d3-455">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="5b3d3-455">NUMERIC_PRECISION</span></span>|<span data-ttu-id="5b3d3-456">Int32</span><span class="sxs-lookup"><span data-stu-id="5b3d3-456">Int32</span></span>|  
|<span data-ttu-id="5b3d3-457">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="5b3d3-457">NUMERIC_SCALE</span></span>|<span data-ttu-id="5b3d3-458">Int16</span><span class="sxs-lookup"><span data-stu-id="5b3d3-458">Int16</span></span>|  
|<span data-ttu-id="5b3d3-459">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="5b3d3-459">DESCRIPTION</span></span>|<span data-ttu-id="5b3d3-460">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-460">String</span></span>|  
|<span data-ttu-id="5b3d3-461">OVERLOAD</span><span class="sxs-lookup"><span data-stu-id="5b3d3-461">OVERLOAD</span></span>|<span data-ttu-id="5b3d3-462">Int16</span><span class="sxs-lookup"><span data-stu-id="5b3d3-462">Int16</span></span>|  
  
### <a name="views"></a><span data-ttu-id="5b3d3-463">ビュー</span><span class="sxs-lookup"><span data-stu-id="5b3d3-463">Views</span></span>  
  
|<span data-ttu-id="5b3d3-464">ColumnName</span><span class="sxs-lookup"><span data-stu-id="5b3d3-464">ColumnName</span></span>|<span data-ttu-id="5b3d3-465">DataType</span><span class="sxs-lookup"><span data-stu-id="5b3d3-465">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="5b3d3-466">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5b3d3-466">TABLE_CATALOG</span></span>|<span data-ttu-id="5b3d3-467">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-467">String</span></span>|  
|<span data-ttu-id="5b3d3-468">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5b3d3-468">TABLE_SCHEMA</span></span>|<span data-ttu-id="5b3d3-469">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-469">String</span></span>|  
|<span data-ttu-id="5b3d3-470">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="5b3d3-470">TABLE_NAME</span></span>|<span data-ttu-id="5b3d3-471">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-471">String</span></span>|  
|<span data-ttu-id="5b3d3-472">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="5b3d3-472">VIEW_DEFINITION</span></span>|<span data-ttu-id="5b3d3-473">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-473">String</span></span>|  
|<span data-ttu-id="5b3d3-474">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="5b3d3-474">CHECK_OPTION</span></span>|<span data-ttu-id="5b3d3-475">Boolean</span><span class="sxs-lookup"><span data-stu-id="5b3d3-475">Boolean</span></span>|  
|<span data-ttu-id="5b3d3-476">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="5b3d3-476">IS_UPDATABLE</span></span>|<span data-ttu-id="5b3d3-477">Boolean</span><span class="sxs-lookup"><span data-stu-id="5b3d3-477">Boolean</span></span>|  
|<span data-ttu-id="5b3d3-478">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="5b3d3-478">DESCRIPTION</span></span>|<span data-ttu-id="5b3d3-479">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-479">String</span></span>|  
|<span data-ttu-id="5b3d3-480">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="5b3d3-480">DATE_CREATED</span></span>|<span data-ttu-id="5b3d3-481">DateTime</span><span class="sxs-lookup"><span data-stu-id="5b3d3-481">DateTime</span></span>|  
|<span data-ttu-id="5b3d3-482">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="5b3d3-482">DATE_MODIFIED</span></span>|<span data-ttu-id="5b3d3-483">DateTime</span><span class="sxs-lookup"><span data-stu-id="5b3d3-483">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="5b3d3-484">Indexes</span><span class="sxs-lookup"><span data-stu-id="5b3d3-484">Indexes</span></span>  
  
|<span data-ttu-id="5b3d3-485">ColumnName</span><span class="sxs-lookup"><span data-stu-id="5b3d3-485">ColumnName</span></span>|<span data-ttu-id="5b3d3-486">DataType</span><span class="sxs-lookup"><span data-stu-id="5b3d3-486">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="5b3d3-487">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5b3d3-487">TABLE_CATALOG</span></span>|<span data-ttu-id="5b3d3-488">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-488">String</span></span>|  
|<span data-ttu-id="5b3d3-489">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5b3d3-489">TABLE_SCHEMA</span></span>|<span data-ttu-id="5b3d3-490">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-490">String</span></span>|  
|<span data-ttu-id="5b3d3-491">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="5b3d3-491">TABLE_NAME</span></span>|<span data-ttu-id="5b3d3-492">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-492">String</span></span>|  
|<span data-ttu-id="5b3d3-493">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5b3d3-493">INDEX_CATALOG</span></span>|<span data-ttu-id="5b3d3-494">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-494">String</span></span>|  
|<span data-ttu-id="5b3d3-495">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5b3d3-495">INDEX_SCHEMA</span></span>|<span data-ttu-id="5b3d3-496">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-496">String</span></span>|  
|<span data-ttu-id="5b3d3-497">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="5b3d3-497">INDEX_NAME</span></span>|<span data-ttu-id="5b3d3-498">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-498">String</span></span>|  
|<span data-ttu-id="5b3d3-499">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="5b3d3-499">PRIMARY_KEY</span></span>|<span data-ttu-id="5b3d3-500">Boolean</span><span class="sxs-lookup"><span data-stu-id="5b3d3-500">Boolean</span></span>|  
|<span data-ttu-id="5b3d3-501">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="5b3d3-501">UNIQUE</span></span>|<span data-ttu-id="5b3d3-502">Boolean</span><span class="sxs-lookup"><span data-stu-id="5b3d3-502">Boolean</span></span>|  
|<span data-ttu-id="5b3d3-503">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="5b3d3-503">CLUSTERED</span></span>|<span data-ttu-id="5b3d3-504">Boolean</span><span class="sxs-lookup"><span data-stu-id="5b3d3-504">Boolean</span></span>|  
|<span data-ttu-id="5b3d3-505">TYPE</span><span class="sxs-lookup"><span data-stu-id="5b3d3-505">TYPE</span></span>|<span data-ttu-id="5b3d3-506">Int32</span><span class="sxs-lookup"><span data-stu-id="5b3d3-506">Int32</span></span>|  
|<span data-ttu-id="5b3d3-507">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="5b3d3-507">FILL_FACTOR</span></span>|<span data-ttu-id="5b3d3-508">Int32</span><span class="sxs-lookup"><span data-stu-id="5b3d3-508">Int32</span></span>|  
|<span data-ttu-id="5b3d3-509">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="5b3d3-509">INITIAL_SIZE</span></span>|<span data-ttu-id="5b3d3-510">Int32</span><span class="sxs-lookup"><span data-stu-id="5b3d3-510">Int32</span></span>|  
|<span data-ttu-id="5b3d3-511">NULLS</span><span class="sxs-lookup"><span data-stu-id="5b3d3-511">NULLS</span></span>|<span data-ttu-id="5b3d3-512">Int32</span><span class="sxs-lookup"><span data-stu-id="5b3d3-512">Int32</span></span>|  
|<span data-ttu-id="5b3d3-513">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="5b3d3-513">SORT_BOOKMARKS</span></span>|<span data-ttu-id="5b3d3-514">Boolean</span><span class="sxs-lookup"><span data-stu-id="5b3d3-514">Boolean</span></span>|  
|<span data-ttu-id="5b3d3-515">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="5b3d3-515">AUTO_UPDATE</span></span>|<span data-ttu-id="5b3d3-516">Boolean</span><span class="sxs-lookup"><span data-stu-id="5b3d3-516">Boolean</span></span>|  
|<span data-ttu-id="5b3d3-517">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="5b3d3-517">NULL_COLLATION</span></span>|<span data-ttu-id="5b3d3-518">Int32</span><span class="sxs-lookup"><span data-stu-id="5b3d3-518">Int32</span></span>|  
|<span data-ttu-id="5b3d3-519">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="5b3d3-519">ORDINAL_POSITION</span></span>|<span data-ttu-id="5b3d3-520">Int64</span><span class="sxs-lookup"><span data-stu-id="5b3d3-520">Int64</span></span>|  
|<span data-ttu-id="5b3d3-521">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="5b3d3-521">COLUMN_NAME</span></span>|<span data-ttu-id="5b3d3-522">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-522">String</span></span>|  
|<span data-ttu-id="5b3d3-523">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="5b3d3-523">COLUMN_GUID</span></span>|<span data-ttu-id="5b3d3-524">Guid</span><span class="sxs-lookup"><span data-stu-id="5b3d3-524">Guid</span></span>|  
|<span data-ttu-id="5b3d3-525">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="5b3d3-525">COLUMN_PROPID</span></span>|<span data-ttu-id="5b3d3-526">Int64</span><span class="sxs-lookup"><span data-stu-id="5b3d3-526">Int64</span></span>|  
|<span data-ttu-id="5b3d3-527">COLLATION</span><span class="sxs-lookup"><span data-stu-id="5b3d3-527">COLLATION</span></span>|<span data-ttu-id="5b3d3-528">Int16</span><span class="sxs-lookup"><span data-stu-id="5b3d3-528">Int16</span></span>|  
|<span data-ttu-id="5b3d3-529">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="5b3d3-529">CARDINALITY</span></span>|<span data-ttu-id="5b3d3-530">Decimal (10 進数型)</span><span class="sxs-lookup"><span data-stu-id="5b3d3-530">Decimal</span></span>|  
|<span data-ttu-id="5b3d3-531">PAGES</span><span class="sxs-lookup"><span data-stu-id="5b3d3-531">PAGES</span></span>|<span data-ttu-id="5b3d3-532">Int32</span><span class="sxs-lookup"><span data-stu-id="5b3d3-532">Int32</span></span>|  
|<span data-ttu-id="5b3d3-533">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="5b3d3-533">FILTER_CONDITION</span></span>|<span data-ttu-id="5b3d3-534">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-534">String</span></span>|  
|<span data-ttu-id="5b3d3-535">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="5b3d3-535">INTEGRATED</span></span>|<span data-ttu-id="5b3d3-536">Boolean</span><span class="sxs-lookup"><span data-stu-id="5b3d3-536">Boolean</span></span>|  
  
## <a name="microsoft-jet-ole-db-provider"></a><span data-ttu-id="5b3d3-537">Microsoft Jet OLE DB Provider</span><span class="sxs-lookup"><span data-stu-id="5b3d3-537">Microsoft Jet OLE DB Provider</span></span>  
 <span data-ttu-id="5b3d3-538">Microsoft Jet OLE DB Driver は、共通のスキーマ コレクションに加えて次のスキーマ コレクションをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="5b3d3-538">The Microsoft Jet OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="5b3d3-539">[テーブル]</span><span class="sxs-lookup"><span data-stu-id="5b3d3-539">Tables</span></span>  
  
-   <span data-ttu-id="5b3d3-540">列</span><span class="sxs-lookup"><span data-stu-id="5b3d3-540">Columns</span></span>  
  
-   <span data-ttu-id="5b3d3-541">手順</span><span class="sxs-lookup"><span data-stu-id="5b3d3-541">Procedures</span></span>  
  
-   <span data-ttu-id="5b3d3-542">ビュー</span><span class="sxs-lookup"><span data-stu-id="5b3d3-542">Views</span></span>  
  
-   <span data-ttu-id="5b3d3-543">Indexes</span><span class="sxs-lookup"><span data-stu-id="5b3d3-543">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="5b3d3-544">[テーブル]</span><span class="sxs-lookup"><span data-stu-id="5b3d3-544">Tables</span></span>  
  
|<span data-ttu-id="5b3d3-545">ColumnName</span><span class="sxs-lookup"><span data-stu-id="5b3d3-545">ColumnName</span></span>|<span data-ttu-id="5b3d3-546">DataType</span><span class="sxs-lookup"><span data-stu-id="5b3d3-546">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="5b3d3-547">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5b3d3-547">TABLE_CATALOG</span></span>|<span data-ttu-id="5b3d3-548">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-548">String</span></span>|  
|<span data-ttu-id="5b3d3-549">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5b3d3-549">TABLE_SCHEMA</span></span>|<span data-ttu-id="5b3d3-550">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-550">String</span></span>|  
|<span data-ttu-id="5b3d3-551">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="5b3d3-551">TABLE_NAME</span></span>|<span data-ttu-id="5b3d3-552">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-552">String</span></span>|  
|<span data-ttu-id="5b3d3-553">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="5b3d3-553">TABLE_TYPE</span></span>|<span data-ttu-id="5b3d3-554">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-554">String</span></span>|  
|<span data-ttu-id="5b3d3-555">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="5b3d3-555">TABLE_GUID</span></span>|<span data-ttu-id="5b3d3-556">Guid</span><span class="sxs-lookup"><span data-stu-id="5b3d3-556">Guid</span></span>|  
|<span data-ttu-id="5b3d3-557">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="5b3d3-557">DESCRIPTION</span></span>|<span data-ttu-id="5b3d3-558">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-558">String</span></span>|  
|<span data-ttu-id="5b3d3-559">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="5b3d3-559">TABLE_PROPID</span></span>|<span data-ttu-id="5b3d3-560">Int64</span><span class="sxs-lookup"><span data-stu-id="5b3d3-560">Int64</span></span>|  
|<span data-ttu-id="5b3d3-561">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="5b3d3-561">DATE_CREATED</span></span>|<span data-ttu-id="5b3d3-562">DateTime</span><span class="sxs-lookup"><span data-stu-id="5b3d3-562">DateTime</span></span>|  
|<span data-ttu-id="5b3d3-563">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="5b3d3-563">DATE_MODIFIED</span></span>|<span data-ttu-id="5b3d3-564">DateTime</span><span class="sxs-lookup"><span data-stu-id="5b3d3-564">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="5b3d3-565">列</span><span class="sxs-lookup"><span data-stu-id="5b3d3-565">Columns</span></span>  
  
|<span data-ttu-id="5b3d3-566">ColumnName</span><span class="sxs-lookup"><span data-stu-id="5b3d3-566">ColumnName</span></span>|<span data-ttu-id="5b3d3-567">DataType</span><span class="sxs-lookup"><span data-stu-id="5b3d3-567">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="5b3d3-568">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5b3d3-568">TABLE_CATALOG</span></span>|<span data-ttu-id="5b3d3-569">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-569">String</span></span>|  
|<span data-ttu-id="5b3d3-570">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5b3d3-570">TABLE_SCHEMA</span></span>|<span data-ttu-id="5b3d3-571">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-571">String</span></span>|  
|<span data-ttu-id="5b3d3-572">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="5b3d3-572">TABLE_NAME</span></span>|<span data-ttu-id="5b3d3-573">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-573">String</span></span>|  
|<span data-ttu-id="5b3d3-574">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="5b3d3-574">COLUMN_NAME</span></span>|<span data-ttu-id="5b3d3-575">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-575">String</span></span>|  
|<span data-ttu-id="5b3d3-576">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="5b3d3-576">COLUMN_GUID</span></span>|<span data-ttu-id="5b3d3-577">Guid</span><span class="sxs-lookup"><span data-stu-id="5b3d3-577">Guid</span></span>|  
|<span data-ttu-id="5b3d3-578">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="5b3d3-578">COLUMN_PROPID</span></span>|<span data-ttu-id="5b3d3-579">Int64</span><span class="sxs-lookup"><span data-stu-id="5b3d3-579">Int64</span></span>|  
|<span data-ttu-id="5b3d3-580">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="5b3d3-580">ORDINAL_POSITION</span></span>|<span data-ttu-id="5b3d3-581">Int64</span><span class="sxs-lookup"><span data-stu-id="5b3d3-581">Int64</span></span>|  
|<span data-ttu-id="5b3d3-582">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="5b3d3-582">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="5b3d3-583">Boolean</span><span class="sxs-lookup"><span data-stu-id="5b3d3-583">Boolean</span></span>|  
|<span data-ttu-id="5b3d3-584">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="5b3d3-584">COLUMN_DEFAULT</span></span>|<span data-ttu-id="5b3d3-585">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-585">String</span></span>|  
|<span data-ttu-id="5b3d3-586">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="5b3d3-586">COLUMN_FLAGS</span></span>|<span data-ttu-id="5b3d3-587">Int64</span><span class="sxs-lookup"><span data-stu-id="5b3d3-587">Int64</span></span>|  
|<span data-ttu-id="5b3d3-588">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="5b3d3-588">IS_NULLABLE</span></span>|<span data-ttu-id="5b3d3-589">Boolean</span><span class="sxs-lookup"><span data-stu-id="5b3d3-589">Boolean</span></span>|  
|<span data-ttu-id="5b3d3-590">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="5b3d3-590">DATA_TYPE</span></span>|<span data-ttu-id="5b3d3-591">Int32</span><span class="sxs-lookup"><span data-stu-id="5b3d3-591">Int32</span></span>|  
|<span data-ttu-id="5b3d3-592">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="5b3d3-592">TYPE_GUID</span></span>|<span data-ttu-id="5b3d3-593">Guid</span><span class="sxs-lookup"><span data-stu-id="5b3d3-593">Guid</span></span>|  
|<span data-ttu-id="5b3d3-594">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="5b3d3-594">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="5b3d3-595">Int64</span><span class="sxs-lookup"><span data-stu-id="5b3d3-595">Int64</span></span>|  
|<span data-ttu-id="5b3d3-596">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="5b3d3-596">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="5b3d3-597">Int64</span><span class="sxs-lookup"><span data-stu-id="5b3d3-597">Int64</span></span>|  
|<span data-ttu-id="5b3d3-598">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="5b3d3-598">NUMERIC_PRECISION</span></span>|<span data-ttu-id="5b3d3-599">Int32</span><span class="sxs-lookup"><span data-stu-id="5b3d3-599">Int32</span></span>|  
|<span data-ttu-id="5b3d3-600">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="5b3d3-600">NUMERIC_SCALE</span></span>|<span data-ttu-id="5b3d3-601">Int16</span><span class="sxs-lookup"><span data-stu-id="5b3d3-601">Int16</span></span>|  
|<span data-ttu-id="5b3d3-602">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="5b3d3-602">DATETIME_PRECISION</span></span>|<span data-ttu-id="5b3d3-603">Int64</span><span class="sxs-lookup"><span data-stu-id="5b3d3-603">Int64</span></span>|  
|<span data-ttu-id="5b3d3-604">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5b3d3-604">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="5b3d3-605">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-605">String</span></span>|  
|<span data-ttu-id="5b3d3-606">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5b3d3-606">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="5b3d3-607">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-607">String</span></span>|  
|<span data-ttu-id="5b3d3-608">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="5b3d3-608">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="5b3d3-609">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-609">String</span></span>|  
|<span data-ttu-id="5b3d3-610">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5b3d3-610">COLLATION_CATALOG</span></span>|<span data-ttu-id="5b3d3-611">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-611">String</span></span>|  
|<span data-ttu-id="5b3d3-612">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5b3d3-612">COLLATION_SCHEMA</span></span>|<span data-ttu-id="5b3d3-613">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-613">String</span></span>|  
|<span data-ttu-id="5b3d3-614">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="5b3d3-614">COLLATION_NAME</span></span>|<span data-ttu-id="5b3d3-615">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-615">String</span></span>|  
|<span data-ttu-id="5b3d3-616">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5b3d3-616">DOMAIN_CATALOG</span></span>|<span data-ttu-id="5b3d3-617">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-617">String</span></span>|  
|<span data-ttu-id="5b3d3-618">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5b3d3-618">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="5b3d3-619">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-619">String</span></span>|  
|<span data-ttu-id="5b3d3-620">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="5b3d3-620">DOMAIN_NAME</span></span>|<span data-ttu-id="5b3d3-621">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-621">String</span></span>|  
|<span data-ttu-id="5b3d3-622">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="5b3d3-622">DESCRIPTION</span></span>|<span data-ttu-id="5b3d3-623">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-623">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="5b3d3-624">手順</span><span class="sxs-lookup"><span data-stu-id="5b3d3-624">Procedures</span></span>  
  
|<span data-ttu-id="5b3d3-625">ColumnName</span><span class="sxs-lookup"><span data-stu-id="5b3d3-625">ColumnName</span></span>|<span data-ttu-id="5b3d3-626">DataType</span><span class="sxs-lookup"><span data-stu-id="5b3d3-626">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="5b3d3-627">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5b3d3-627">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="5b3d3-628">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-628">String</span></span>|  
|<span data-ttu-id="5b3d3-629">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5b3d3-629">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="5b3d3-630">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-630">String</span></span>|  
|<span data-ttu-id="5b3d3-631">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="5b3d3-631">PROCEDURE_NAME</span></span>|<span data-ttu-id="5b3d3-632">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-632">String</span></span>|  
|<span data-ttu-id="5b3d3-633">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="5b3d3-633">PROCEDURE_TYPE</span></span>|<span data-ttu-id="5b3d3-634">Int16</span><span class="sxs-lookup"><span data-stu-id="5b3d3-634">Int16</span></span>|  
|<span data-ttu-id="5b3d3-635">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="5b3d3-635">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="5b3d3-636">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-636">String</span></span>|  
|<span data-ttu-id="5b3d3-637">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="5b3d3-637">DESCRIPTION</span></span>|<span data-ttu-id="5b3d3-638">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-638">String</span></span>|  
|<span data-ttu-id="5b3d3-639">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="5b3d3-639">DATE_CREATED</span></span>|<span data-ttu-id="5b3d3-640">DateTime</span><span class="sxs-lookup"><span data-stu-id="5b3d3-640">DateTime</span></span>|  
|<span data-ttu-id="5b3d3-641">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="5b3d3-641">DATE_MODIFIED</span></span>|<span data-ttu-id="5b3d3-642">DateTime</span><span class="sxs-lookup"><span data-stu-id="5b3d3-642">DateTime</span></span>|  
  
### <a name="views"></a><span data-ttu-id="5b3d3-643">ビュー</span><span class="sxs-lookup"><span data-stu-id="5b3d3-643">Views</span></span>  
  
|<span data-ttu-id="5b3d3-644">ColumnName</span><span class="sxs-lookup"><span data-stu-id="5b3d3-644">ColumnName</span></span>|<span data-ttu-id="5b3d3-645">DataType</span><span class="sxs-lookup"><span data-stu-id="5b3d3-645">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="5b3d3-646">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5b3d3-646">TABLE_CATALOG</span></span>|<span data-ttu-id="5b3d3-647">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-647">String</span></span>|  
|<span data-ttu-id="5b3d3-648">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5b3d3-648">TABLE_SCHEMA</span></span>|<span data-ttu-id="5b3d3-649">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-649">String</span></span>|  
|<span data-ttu-id="5b3d3-650">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="5b3d3-650">TABLE_NAME</span></span>|<span data-ttu-id="5b3d3-651">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-651">String</span></span>|  
|<span data-ttu-id="5b3d3-652">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="5b3d3-652">VIEW_DEFINITION</span></span>|<span data-ttu-id="5b3d3-653">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-653">String</span></span>|  
|<span data-ttu-id="5b3d3-654">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="5b3d3-654">CHECK_OPTION</span></span>|<span data-ttu-id="5b3d3-655">Boolean</span><span class="sxs-lookup"><span data-stu-id="5b3d3-655">Boolean</span></span>|  
|<span data-ttu-id="5b3d3-656">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="5b3d3-656">IS_UPDATABLE</span></span>|<span data-ttu-id="5b3d3-657">Boolean</span><span class="sxs-lookup"><span data-stu-id="5b3d3-657">Boolean</span></span>|  
|<span data-ttu-id="5b3d3-658">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="5b3d3-658">DESCRIPTION</span></span>|<span data-ttu-id="5b3d3-659">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-659">String</span></span>|  
|<span data-ttu-id="5b3d3-660">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="5b3d3-660">DATE_CREATED</span></span>|<span data-ttu-id="5b3d3-661">DateTime</span><span class="sxs-lookup"><span data-stu-id="5b3d3-661">DateTime</span></span>|  
|<span data-ttu-id="5b3d3-662">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="5b3d3-662">DATE_MODIFIED</span></span>|<span data-ttu-id="5b3d3-663">DateTime</span><span class="sxs-lookup"><span data-stu-id="5b3d3-663">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="5b3d3-664">Indexes</span><span class="sxs-lookup"><span data-stu-id="5b3d3-664">Indexes</span></span>  
  
|<span data-ttu-id="5b3d3-665">ColumnName</span><span class="sxs-lookup"><span data-stu-id="5b3d3-665">ColumnName</span></span>|<span data-ttu-id="5b3d3-666">DataType</span><span class="sxs-lookup"><span data-stu-id="5b3d3-666">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="5b3d3-667">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5b3d3-667">TABLE_CATALOG</span></span>|<span data-ttu-id="5b3d3-668">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-668">String</span></span>|  
|<span data-ttu-id="5b3d3-669">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5b3d3-669">TABLE_SCHEMA</span></span>|<span data-ttu-id="5b3d3-670">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-670">String</span></span>|  
|<span data-ttu-id="5b3d3-671">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="5b3d3-671">TABLE_NAME</span></span>|<span data-ttu-id="5b3d3-672">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-672">String</span></span>|  
|<span data-ttu-id="5b3d3-673">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5b3d3-673">INDEX_CATALOG</span></span>|<span data-ttu-id="5b3d3-674">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-674">String</span></span>|  
|<span data-ttu-id="5b3d3-675">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5b3d3-675">INDEX_SCHEMA</span></span>|<span data-ttu-id="5b3d3-676">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-676">String</span></span>|  
|<span data-ttu-id="5b3d3-677">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="5b3d3-677">INDEX_NAME</span></span>|<span data-ttu-id="5b3d3-678">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-678">String</span></span>|  
|<span data-ttu-id="5b3d3-679">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="5b3d3-679">PRIMARY_KEY</span></span>|<span data-ttu-id="5b3d3-680">Boolean</span><span class="sxs-lookup"><span data-stu-id="5b3d3-680">Boolean</span></span>|  
|<span data-ttu-id="5b3d3-681">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="5b3d3-681">UNIQUE</span></span>|<span data-ttu-id="5b3d3-682">Boolean</span><span class="sxs-lookup"><span data-stu-id="5b3d3-682">Boolean</span></span>|  
|<span data-ttu-id="5b3d3-683">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="5b3d3-683">CLUSTERED</span></span>|<span data-ttu-id="5b3d3-684">Boolean</span><span class="sxs-lookup"><span data-stu-id="5b3d3-684">Boolean</span></span>|  
|<span data-ttu-id="5b3d3-685">TYPE</span><span class="sxs-lookup"><span data-stu-id="5b3d3-685">TYPE</span></span>|<span data-ttu-id="5b3d3-686">Int32</span><span class="sxs-lookup"><span data-stu-id="5b3d3-686">Int32</span></span>|  
|<span data-ttu-id="5b3d3-687">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="5b3d3-687">FILL_FACTOR</span></span>|<span data-ttu-id="5b3d3-688">Int32</span><span class="sxs-lookup"><span data-stu-id="5b3d3-688">Int32</span></span>|  
|<span data-ttu-id="5b3d3-689">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="5b3d3-689">INITIAL_SIZE</span></span>|<span data-ttu-id="5b3d3-690">Int32</span><span class="sxs-lookup"><span data-stu-id="5b3d3-690">Int32</span></span>|  
|<span data-ttu-id="5b3d3-691">NULLS</span><span class="sxs-lookup"><span data-stu-id="5b3d3-691">NULLS</span></span>|<span data-ttu-id="5b3d3-692">Int32</span><span class="sxs-lookup"><span data-stu-id="5b3d3-692">Int32</span></span>|  
|<span data-ttu-id="5b3d3-693">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="5b3d3-693">SORT_BOOKMARKS</span></span>|<span data-ttu-id="5b3d3-694">Boolean</span><span class="sxs-lookup"><span data-stu-id="5b3d3-694">Boolean</span></span>|  
|<span data-ttu-id="5b3d3-695">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="5b3d3-695">AUTO_UPDATE</span></span>|<span data-ttu-id="5b3d3-696">Boolean</span><span class="sxs-lookup"><span data-stu-id="5b3d3-696">Boolean</span></span>|  
|<span data-ttu-id="5b3d3-697">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="5b3d3-697">NULL_COLLATION</span></span>|<span data-ttu-id="5b3d3-698">Int32</span><span class="sxs-lookup"><span data-stu-id="5b3d3-698">Int32</span></span>|  
|<span data-ttu-id="5b3d3-699">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="5b3d3-699">ORDINAL_POSITION</span></span>|<span data-ttu-id="5b3d3-700">Int64</span><span class="sxs-lookup"><span data-stu-id="5b3d3-700">Int64</span></span>|  
|<span data-ttu-id="5b3d3-701">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="5b3d3-701">COLUMN_NAME</span></span>|<span data-ttu-id="5b3d3-702">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-702">String</span></span>|  
|<span data-ttu-id="5b3d3-703">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="5b3d3-703">COLUMN_GUID</span></span>|<span data-ttu-id="5b3d3-704">Guid</span><span class="sxs-lookup"><span data-stu-id="5b3d3-704">Guid</span></span>|  
|<span data-ttu-id="5b3d3-705">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="5b3d3-705">COLUMN_PROPID</span></span>|<span data-ttu-id="5b3d3-706">Int64</span><span class="sxs-lookup"><span data-stu-id="5b3d3-706">Int64</span></span>|  
|<span data-ttu-id="5b3d3-707">COLLATION</span><span class="sxs-lookup"><span data-stu-id="5b3d3-707">COLLATION</span></span>|<span data-ttu-id="5b3d3-708">Int16</span><span class="sxs-lookup"><span data-stu-id="5b3d3-708">Int16</span></span>|  
|<span data-ttu-id="5b3d3-709">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="5b3d3-709">CARDINALITY</span></span>|<span data-ttu-id="5b3d3-710">Decimal (10 進数型)</span><span class="sxs-lookup"><span data-stu-id="5b3d3-710">Decimal</span></span>|  
|<span data-ttu-id="5b3d3-711">PAGES</span><span class="sxs-lookup"><span data-stu-id="5b3d3-711">PAGES</span></span>|<span data-ttu-id="5b3d3-712">Int32</span><span class="sxs-lookup"><span data-stu-id="5b3d3-712">Int32</span></span>|  
|<span data-ttu-id="5b3d3-713">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="5b3d3-713">FILTER_CONDITION</span></span>|<span data-ttu-id="5b3d3-714">String</span><span class="sxs-lookup"><span data-stu-id="5b3d3-714">String</span></span>|  
|<span data-ttu-id="5b3d3-715">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="5b3d3-715">INTEGRATED</span></span>|<span data-ttu-id="5b3d3-716">ブール型</span><span class="sxs-lookup"><span data-stu-id="5b3d3-716">Boolean</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5b3d3-717">参照</span><span class="sxs-lookup"><span data-stu-id="5b3d3-717">See Also</span></span>  
 [<span data-ttu-id="5b3d3-718">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="5b3d3-718">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
