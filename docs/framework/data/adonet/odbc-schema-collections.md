---
title: "ODBC スキーマ コレクション"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1bb126a5-ceec-4649-a4bc-8aa19e801046
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 45cfed80decc2336c5a2bacf24fd075c2b81c531
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="odbc-schema-collections"></a><span data-ttu-id="cbc84-102">ODBC スキーマ コレクション</span><span class="sxs-lookup"><span data-stu-id="cbc84-102">ODBC Schema Collections</span></span>
<span data-ttu-id="cbc84-103">ここでは、Microsoft SQL Server、Oracle、および Microsoft Jet 用の各 ODBC ドライバーでのスキーマ コレクションのサポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="cbc84-103">This section discusses schema collection support for the ODBC drivers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-odbc-driver"></a><span data-ttu-id="cbc84-104">Microsoft SQL Server ODBC Driver</span><span class="sxs-lookup"><span data-stu-id="cbc84-104">Microsoft SQL Server ODBC Driver</span></span>  
 <span data-ttu-id="cbc84-105">Microsoft SQL Server ODBC Driver は、共通のスキーマ コレクションに加えて次の特定のスキーマ コレクションをサポートします。</span><span class="sxs-lookup"><span data-stu-id="cbc84-105">The Microsoft SQL Server ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="cbc84-106">[テーブル]</span><span class="sxs-lookup"><span data-stu-id="cbc84-106">Tables</span></span>  
  
-   <span data-ttu-id="cbc84-107">Indexes</span><span class="sxs-lookup"><span data-stu-id="cbc84-107">Indexes</span></span>  
  
-   <span data-ttu-id="cbc84-108">列</span><span class="sxs-lookup"><span data-stu-id="cbc84-108">Columns</span></span>  
  
-   <span data-ttu-id="cbc84-109">手順</span><span class="sxs-lookup"><span data-stu-id="cbc84-109">Procedures</span></span>  
  
-   <span data-ttu-id="cbc84-110">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="cbc84-110">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="cbc84-111">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="cbc84-111">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="cbc84-112">ビュー</span><span class="sxs-lookup"><span data-stu-id="cbc84-112">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="cbc84-113">Tables と Views</span><span class="sxs-lookup"><span data-stu-id="cbc84-113">Tables and Views</span></span>  
  
|<span data-ttu-id="cbc84-114">ColumnName</span><span class="sxs-lookup"><span data-stu-id="cbc84-114">ColumnName</span></span>|<span data-ttu-id="cbc84-115">DataType</span><span class="sxs-lookup"><span data-stu-id="cbc84-115">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="cbc84-116">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="cbc84-116">TABLE_CAT</span></span>|<span data-ttu-id="cbc84-117">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-117">String</span></span>|  
|<span data-ttu-id="cbc84-118">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="cbc84-118">TABLE_SCHEM</span></span>|<span data-ttu-id="cbc84-119">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-119">String</span></span>|  
|<span data-ttu-id="cbc84-120">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="cbc84-120">TABLE_NAME</span></span>|<span data-ttu-id="cbc84-121">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-121">String</span></span>|  
|<span data-ttu-id="cbc84-122">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="cbc84-122">TABLE_TYPE</span></span>|<span data-ttu-id="cbc84-123">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-123">String</span></span>|  
|<span data-ttu-id="cbc84-124">REMARKS</span><span class="sxs-lookup"><span data-stu-id="cbc84-124">REMARKS</span></span>|<span data-ttu-id="cbc84-125">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-125">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="cbc84-126">Indexes</span><span class="sxs-lookup"><span data-stu-id="cbc84-126">Indexes</span></span>  
  
|<span data-ttu-id="cbc84-127">ColumnName</span><span class="sxs-lookup"><span data-stu-id="cbc84-127">ColumnName</span></span>|<span data-ttu-id="cbc84-128">DataType</span><span class="sxs-lookup"><span data-stu-id="cbc84-128">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="cbc84-129">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="cbc84-129">TABLE_CAT</span></span>|<span data-ttu-id="cbc84-130">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-130">String</span></span>|  
|<span data-ttu-id="cbc84-131">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="cbc84-131">TABLE_SCHEM</span></span>|<span data-ttu-id="cbc84-132">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-132">String</span></span>|  
|<span data-ttu-id="cbc84-133">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="cbc84-133">TABLE_NAME</span></span>|<span data-ttu-id="cbc84-134">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-134">String</span></span>|  
|<span data-ttu-id="cbc84-135">NON_UNIQUE</span><span class="sxs-lookup"><span data-stu-id="cbc84-135">NON_UNIQUE</span></span>|<span data-ttu-id="cbc84-136">Int16</span><span class="sxs-lookup"><span data-stu-id="cbc84-136">Int16</span></span>|  
|<span data-ttu-id="cbc84-137">INDEX_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="cbc84-137">INDEX_QUALIFIER</span></span>|<span data-ttu-id="cbc84-138">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-138">String</span></span>|  
|<span data-ttu-id="cbc84-139">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="cbc84-139">INDEX_NAME</span></span>|<span data-ttu-id="cbc84-140">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-140">String</span></span>|  
|<span data-ttu-id="cbc84-141">TYPE</span><span class="sxs-lookup"><span data-stu-id="cbc84-141">TYPE</span></span>|<span data-ttu-id="cbc84-142">Int16</span><span class="sxs-lookup"><span data-stu-id="cbc84-142">Int16</span></span>|  
|<span data-ttu-id="cbc84-143">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="cbc84-143">ORDINAL_POSITION</span></span>|<span data-ttu-id="cbc84-144">Int16</span><span class="sxs-lookup"><span data-stu-id="cbc84-144">Int16</span></span>|  
|<span data-ttu-id="cbc84-145">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="cbc84-145">COLUMN_NAME</span></span>|<span data-ttu-id="cbc84-146">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-146">String</span></span>|  
|<span data-ttu-id="cbc84-147">ASC_OR_DESC</span><span class="sxs-lookup"><span data-stu-id="cbc84-147">ASC_OR_DESC</span></span>|<span data-ttu-id="cbc84-148">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-148">String</span></span>|  
|<span data-ttu-id="cbc84-149">CARDINATLITY</span><span class="sxs-lookup"><span data-stu-id="cbc84-149">CARDINATLITY</span></span>|<span data-ttu-id="cbc84-150">Int32</span><span class="sxs-lookup"><span data-stu-id="cbc84-150">Int32</span></span>|  
|<span data-ttu-id="cbc84-151">PAGES</span><span class="sxs-lookup"><span data-stu-id="cbc84-151">PAGES</span></span>|<span data-ttu-id="cbc84-152">Int32</span><span class="sxs-lookup"><span data-stu-id="cbc84-152">Int32</span></span>|  
|<span data-ttu-id="cbc84-153">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="cbc84-153">FILTER_CONDITION</span></span>|<span data-ttu-id="cbc84-154">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-154">String</span></span>|  
|<span data-ttu-id="cbc84-155">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="cbc84-155">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="cbc84-156">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-156">String</span></span>|  
|<span data-ttu-id="cbc84-157">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="cbc84-157">SS_DATA_TYPE</span></span>|<span data-ttu-id="cbc84-158">Byte</span><span class="sxs-lookup"><span data-stu-id="cbc84-158">Byte</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="cbc84-159">列</span><span class="sxs-lookup"><span data-stu-id="cbc84-159">Columns</span></span>  
  
|<span data-ttu-id="cbc84-160">ColumnName</span><span class="sxs-lookup"><span data-stu-id="cbc84-160">ColumnName</span></span>|<span data-ttu-id="cbc84-161">DataType</span><span class="sxs-lookup"><span data-stu-id="cbc84-161">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="cbc84-162">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="cbc84-162">TABLE_CAT</span></span>|<span data-ttu-id="cbc84-163">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-163">String</span></span>|  
|<span data-ttu-id="cbc84-164">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="cbc84-164">TABLE_SCHEM</span></span>|<span data-ttu-id="cbc84-165">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-165">String</span></span>|  
|<span data-ttu-id="cbc84-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="cbc84-166">TABLE_NAME</span></span>|<span data-ttu-id="cbc84-167">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-167">String</span></span>|  
|<span data-ttu-id="cbc84-168">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="cbc84-168">COLUMN_NAME</span></span>|<span data-ttu-id="cbc84-169">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-169">String</span></span>|  
|<span data-ttu-id="cbc84-170">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="cbc84-170">DATA_TYPE</span></span>|<span data-ttu-id="cbc84-171">Int16</span><span class="sxs-lookup"><span data-stu-id="cbc84-171">Int16</span></span>|  
|<span data-ttu-id="cbc84-172">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="cbc84-172">TYPE_NAME</span></span>|<span data-ttu-id="cbc84-173">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-173">String</span></span>|  
|<span data-ttu-id="cbc84-174">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="cbc84-174">COLUMN_SIZE</span></span>|<span data-ttu-id="cbc84-175">Int32</span><span class="sxs-lookup"><span data-stu-id="cbc84-175">Int32</span></span>|  
|<span data-ttu-id="cbc84-176">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="cbc84-176">BUFFER_LENGTH</span></span>|<span data-ttu-id="cbc84-177">Int32</span><span class="sxs-lookup"><span data-stu-id="cbc84-177">Int32</span></span>|  
|<span data-ttu-id="cbc84-178">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="cbc84-178">DECIMAL_DIGITS</span></span>|<span data-ttu-id="cbc84-179">Int16</span><span class="sxs-lookup"><span data-stu-id="cbc84-179">Int16</span></span>|  
|<span data-ttu-id="cbc84-180">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="cbc84-180">NUM_PREC_RADIX</span></span>|<span data-ttu-id="cbc84-181">Int16</span><span class="sxs-lookup"><span data-stu-id="cbc84-181">Int16</span></span>|  
|<span data-ttu-id="cbc84-182">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="cbc84-182">NULLABLE</span></span>|<span data-ttu-id="cbc84-183">Int16</span><span class="sxs-lookup"><span data-stu-id="cbc84-183">Int16</span></span>|  
|<span data-ttu-id="cbc84-184">REMARKS</span><span class="sxs-lookup"><span data-stu-id="cbc84-184">REMARKS</span></span>|<span data-ttu-id="cbc84-185">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-185">String</span></span>|  
|<span data-ttu-id="cbc84-186">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="cbc84-186">COLUMN_DEF</span></span>|<span data-ttu-id="cbc84-187">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-187">String</span></span>|  
|<span data-ttu-id="cbc84-188">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="cbc84-188">SQL_DATA_TYPE</span></span>|<span data-ttu-id="cbc84-189">Int16</span><span class="sxs-lookup"><span data-stu-id="cbc84-189">Int16</span></span>|  
|<span data-ttu-id="cbc84-190">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="cbc84-190">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="cbc84-191">Int16</span><span class="sxs-lookup"><span data-stu-id="cbc84-191">Int16</span></span>|  
|<span data-ttu-id="cbc84-192">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="cbc84-192">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="cbc84-193">Int32</span><span class="sxs-lookup"><span data-stu-id="cbc84-193">Int32</span></span>|  
|<span data-ttu-id="cbc84-194">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="cbc84-194">ORDINAL_POSITION</span></span>|<span data-ttu-id="cbc84-195">Int32</span><span class="sxs-lookup"><span data-stu-id="cbc84-195">Int32</span></span>|  
|<span data-ttu-id="cbc84-196">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="cbc84-196">IS_NULLABLE</span></span>|<span data-ttu-id="cbc84-197">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-197">String</span></span>|  
|<span data-ttu-id="cbc84-198">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="cbc84-198">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="cbc84-199">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-199">String</span></span>|  
|<span data-ttu-id="cbc84-200">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="cbc84-200">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="cbc84-201">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-201">String</span></span>|  
|<span data-ttu-id="cbc84-202">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="cbc84-202">SS_DATA_TYPE</span></span>|<span data-ttu-id="cbc84-203">Byte</span><span class="sxs-lookup"><span data-stu-id="cbc84-203">Byte</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="cbc84-204">手順</span><span class="sxs-lookup"><span data-stu-id="cbc84-204">Procedures</span></span>  
  
|<span data-ttu-id="cbc84-205">ColumnName</span><span class="sxs-lookup"><span data-stu-id="cbc84-205">ColumnName</span></span>|<span data-ttu-id="cbc84-206">DataType</span><span class="sxs-lookup"><span data-stu-id="cbc84-206">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="cbc84-207">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="cbc84-207">PROCEDURE_CAT</span></span>|<span data-ttu-id="cbc84-208">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-208">String</span></span>|  
|<span data-ttu-id="cbc84-209">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="cbc84-209">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="cbc84-210">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-210">String</span></span>|  
|<span data-ttu-id="cbc84-211">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="cbc84-211">PROCEDURE_NAME</span></span>|<span data-ttu-id="cbc84-212">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-212">String</span></span>|  
|<span data-ttu-id="cbc84-213">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="cbc84-213">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="cbc84-214">Int32</span><span class="sxs-lookup"><span data-stu-id="cbc84-214">Int32</span></span>|  
|<span data-ttu-id="cbc84-215">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="cbc84-215">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="cbc84-216">Int32</span><span class="sxs-lookup"><span data-stu-id="cbc84-216">Int32</span></span>|  
|<span data-ttu-id="cbc84-217">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="cbc84-217">NUM_RESULT_SETS</span></span>|<span data-ttu-id="cbc84-218">Int32</span><span class="sxs-lookup"><span data-stu-id="cbc84-218">Int32</span></span>|  
|<span data-ttu-id="cbc84-219">REMARKS</span><span class="sxs-lookup"><span data-stu-id="cbc84-219">REMARKS</span></span>|<span data-ttu-id="cbc84-220">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-220">String</span></span>|  
|<span data-ttu-id="cbc84-221">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="cbc84-221">PROCEDURE_TYPE</span></span>|<span data-ttu-id="cbc84-222">Int16</span><span class="sxs-lookup"><span data-stu-id="cbc84-222">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="cbc84-223">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="cbc84-223">ProcedureColumns</span></span>  
  
|<span data-ttu-id="cbc84-224">ColumnName</span><span class="sxs-lookup"><span data-stu-id="cbc84-224">ColumnName</span></span>|<span data-ttu-id="cbc84-225">DataType</span><span class="sxs-lookup"><span data-stu-id="cbc84-225">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="cbc84-226">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="cbc84-226">PROCEDURE_CAT</span></span>|<span data-ttu-id="cbc84-227">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-227">String</span></span>|  
|<span data-ttu-id="cbc84-228">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="cbc84-228">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="cbc84-229">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-229">String</span></span>|  
|<span data-ttu-id="cbc84-230">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="cbc84-230">PROCEDURE_NAME</span></span>|<span data-ttu-id="cbc84-231">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-231">String</span></span>|  
|<span data-ttu-id="cbc84-232">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="cbc84-232">COLUMN_NAME</span></span>|<span data-ttu-id="cbc84-233">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-233">String</span></span>|  
|<span data-ttu-id="cbc84-234">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="cbc84-234">COLUMN_TYPE</span></span>|<span data-ttu-id="cbc84-235">Int16</span><span class="sxs-lookup"><span data-stu-id="cbc84-235">Int16</span></span>|  
|<span data-ttu-id="cbc84-236">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="cbc84-236">DATA_TYPE</span></span>|<span data-ttu-id="cbc84-237">Int16</span><span class="sxs-lookup"><span data-stu-id="cbc84-237">Int16</span></span>|  
|<span data-ttu-id="cbc84-238">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="cbc84-238">TYPE_NAME</span></span>|<span data-ttu-id="cbc84-239">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-239">String</span></span>|  
|<span data-ttu-id="cbc84-240">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="cbc84-240">COLUMN_SIZE</span></span>|<span data-ttu-id="cbc84-241">Int32</span><span class="sxs-lookup"><span data-stu-id="cbc84-241">Int32</span></span>|  
|<span data-ttu-id="cbc84-242">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="cbc84-242">BUFFER_LENGTH</span></span>|<span data-ttu-id="cbc84-243">Int32</span><span class="sxs-lookup"><span data-stu-id="cbc84-243">Int32</span></span>|  
|<span data-ttu-id="cbc84-244">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="cbc84-244">DECIMAL_DIGITS</span></span>|<span data-ttu-id="cbc84-245">Int16</span><span class="sxs-lookup"><span data-stu-id="cbc84-245">Int16</span></span>|  
|<span data-ttu-id="cbc84-246">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="cbc84-246">NUM_PREC_RADIX</span></span>|<span data-ttu-id="cbc84-247">Int16</span><span class="sxs-lookup"><span data-stu-id="cbc84-247">Int16</span></span>|  
|<span data-ttu-id="cbc84-248">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="cbc84-248">NULLABLE</span></span>|<span data-ttu-id="cbc84-249">Int16</span><span class="sxs-lookup"><span data-stu-id="cbc84-249">Int16</span></span>|  
|<span data-ttu-id="cbc84-250">REMARKS</span><span class="sxs-lookup"><span data-stu-id="cbc84-250">REMARKS</span></span>|<span data-ttu-id="cbc84-251">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-251">String</span></span>|  
|<span data-ttu-id="cbc84-252">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="cbc84-252">COLUMN_DEF</span></span>|<span data-ttu-id="cbc84-253">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-253">String</span></span>|  
|<span data-ttu-id="cbc84-254">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="cbc84-254">SQL_DATA_TYPE</span></span>|<span data-ttu-id="cbc84-255">Int16</span><span class="sxs-lookup"><span data-stu-id="cbc84-255">Int16</span></span>|  
|<span data-ttu-id="cbc84-256">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="cbc84-256">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="cbc84-257">Int16</span><span class="sxs-lookup"><span data-stu-id="cbc84-257">Int16</span></span>|  
|<span data-ttu-id="cbc84-258">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="cbc84-258">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="cbc84-259">Int32</span><span class="sxs-lookup"><span data-stu-id="cbc84-259">Int32</span></span>|  
|<span data-ttu-id="cbc84-260">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="cbc84-260">ORDINAL_POSITION</span></span>|<span data-ttu-id="cbc84-261">Int32</span><span class="sxs-lookup"><span data-stu-id="cbc84-261">Int32</span></span>|  
|<span data-ttu-id="cbc84-262">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="cbc84-262">IS_NULLABLE</span></span>|<span data-ttu-id="cbc84-263">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-263">String</span></span>|  
|<span data-ttu-id="cbc84-264">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="cbc84-264">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="cbc84-265">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-265">String</span></span>|  
|<span data-ttu-id="cbc84-266">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="cbc84-266">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="cbc84-267">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-267">String</span></span>|  
|<span data-ttu-id="cbc84-268">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="cbc84-268">SS_DATA_TYPE</span></span>|<span data-ttu-id="cbc84-269">Byte</span><span class="sxs-lookup"><span data-stu-id="cbc84-269">Byte</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="cbc84-270">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="cbc84-270">ProcedureParameters</span></span>  
  
|<span data-ttu-id="cbc84-271">ColumnName</span><span class="sxs-lookup"><span data-stu-id="cbc84-271">ColumnName</span></span>|<span data-ttu-id="cbc84-272">DataType</span><span class="sxs-lookup"><span data-stu-id="cbc84-272">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="cbc84-273">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="cbc84-273">PROCEDURE_CAT</span></span>|<span data-ttu-id="cbc84-274">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-274">String</span></span>|  
|<span data-ttu-id="cbc84-275">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="cbc84-275">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="cbc84-276">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-276">String</span></span>|  
|<span data-ttu-id="cbc84-277">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="cbc84-277">PROCEDURE_NAME</span></span>|<span data-ttu-id="cbc84-278">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-278">String</span></span>|  
|<span data-ttu-id="cbc84-279">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="cbc84-279">COLUMN_NAME</span></span>|<span data-ttu-id="cbc84-280">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-280">String</span></span>|  
|<span data-ttu-id="cbc84-281">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="cbc84-281">COLUMN_TYPE</span></span>|<span data-ttu-id="cbc84-282">Int16</span><span class="sxs-lookup"><span data-stu-id="cbc84-282">Int16</span></span>|  
|<span data-ttu-id="cbc84-283">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="cbc84-283">DATA_TYPE</span></span>|<span data-ttu-id="cbc84-284">Int16</span><span class="sxs-lookup"><span data-stu-id="cbc84-284">Int16</span></span>|  
|<span data-ttu-id="cbc84-285">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="cbc84-285">TYPE_NAME</span></span>|<span data-ttu-id="cbc84-286">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-286">String</span></span>|  
|<span data-ttu-id="cbc84-287">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="cbc84-287">COLUMN_SIZE</span></span>|<span data-ttu-id="cbc84-288">Int32</span><span class="sxs-lookup"><span data-stu-id="cbc84-288">Int32</span></span>|  
|<span data-ttu-id="cbc84-289">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="cbc84-289">BUFFER_LENGTH</span></span>|<span data-ttu-id="cbc84-290">Int32</span><span class="sxs-lookup"><span data-stu-id="cbc84-290">Int32</span></span>|  
|<span data-ttu-id="cbc84-291">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="cbc84-291">DECIMAL_DIGITS</span></span>|<span data-ttu-id="cbc84-292">Int16</span><span class="sxs-lookup"><span data-stu-id="cbc84-292">Int16</span></span>|  
|<span data-ttu-id="cbc84-293">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="cbc84-293">NUM_PREC_RADIX</span></span>|<span data-ttu-id="cbc84-294">Int16</span><span class="sxs-lookup"><span data-stu-id="cbc84-294">Int16</span></span>|  
|<span data-ttu-id="cbc84-295">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="cbc84-295">NULLABLE</span></span>|<span data-ttu-id="cbc84-296">Int16</span><span class="sxs-lookup"><span data-stu-id="cbc84-296">Int16</span></span>|  
|<span data-ttu-id="cbc84-297">REMARKS</span><span class="sxs-lookup"><span data-stu-id="cbc84-297">REMARKS</span></span>|<span data-ttu-id="cbc84-298">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-298">String</span></span>|  
|<span data-ttu-id="cbc84-299">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="cbc84-299">COLUMN_DEF</span></span>|<span data-ttu-id="cbc84-300">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-300">String</span></span>|  
|<span data-ttu-id="cbc84-301">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="cbc84-301">SQL_DATA_TYPE</span></span>|<span data-ttu-id="cbc84-302">Int16</span><span class="sxs-lookup"><span data-stu-id="cbc84-302">Int16</span></span>|  
|<span data-ttu-id="cbc84-303">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="cbc84-303">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="cbc84-304">Int16</span><span class="sxs-lookup"><span data-stu-id="cbc84-304">Int16</span></span>|  
|<span data-ttu-id="cbc84-305">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="cbc84-305">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="cbc84-306">Int32</span><span class="sxs-lookup"><span data-stu-id="cbc84-306">Int32</span></span>|  
|<span data-ttu-id="cbc84-307">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="cbc84-307">ORDINAL_POSITION</span></span>|<span data-ttu-id="cbc84-308">Int32</span><span class="sxs-lookup"><span data-stu-id="cbc84-308">Int32</span></span>|  
|<span data-ttu-id="cbc84-309">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="cbc84-309">IS_NULLABLE</span></span>|<span data-ttu-id="cbc84-310">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-310">String</span></span>|  
|<span data-ttu-id="cbc84-311">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="cbc84-311">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="cbc84-312">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-312">String</span></span>|  
|<span data-ttu-id="cbc84-313">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="cbc84-313">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="cbc84-314">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-314">String</span></span>|  
|<span data-ttu-id="cbc84-315">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="cbc84-315">SS_DATA_TYPE</span></span>|<span data-ttu-id="cbc84-316">Byte</span><span class="sxs-lookup"><span data-stu-id="cbc84-316">Byte</span></span>|  
  
## <a name="microsoft-oracle-odbc-driver"></a><span data-ttu-id="cbc84-317">Microsoft Oracle ODBC Driver</span><span class="sxs-lookup"><span data-stu-id="cbc84-317">Microsoft Oracle ODBC Driver</span></span>  
 <span data-ttu-id="cbc84-318">Microsoft SQL Server Oracle ODBC Driver は、共通のスキーマ コレクションに加えて次の特定のスキーマ コレクションをサポートします。</span><span class="sxs-lookup"><span data-stu-id="cbc84-318">The Microsoft SQL Server Oracle ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="cbc84-319">[テーブル]</span><span class="sxs-lookup"><span data-stu-id="cbc84-319">Tables</span></span>  
  
-   <span data-ttu-id="cbc84-320">列</span><span class="sxs-lookup"><span data-stu-id="cbc84-320">Columns</span></span>  
  
-   <span data-ttu-id="cbc84-321">手順</span><span class="sxs-lookup"><span data-stu-id="cbc84-321">Procedures</span></span>  
  
-   <span data-ttu-id="cbc84-322">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="cbc84-322">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="cbc84-323">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="cbc84-323">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="cbc84-324">ビュー</span><span class="sxs-lookup"><span data-stu-id="cbc84-324">Views</span></span>  
  
-   <span data-ttu-id="cbc84-325">Indexes</span><span class="sxs-lookup"><span data-stu-id="cbc84-325">Indexes</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="cbc84-326">Tables と Views</span><span class="sxs-lookup"><span data-stu-id="cbc84-326">Tables and Views</span></span>  
  
|<span data-ttu-id="cbc84-327">ColumnName</span><span class="sxs-lookup"><span data-stu-id="cbc84-327">ColumnName</span></span>|<span data-ttu-id="cbc84-328">DataType</span><span class="sxs-lookup"><span data-stu-id="cbc84-328">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="cbc84-329">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="cbc84-329">TABLE_QUALIFIER</span></span>|<span data-ttu-id="cbc84-330">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-330">String</span></span>|  
|<span data-ttu-id="cbc84-331">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="cbc84-331">TABLE_OWNER</span></span>|<span data-ttu-id="cbc84-332">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-332">String</span></span>|  
|<span data-ttu-id="cbc84-333">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="cbc84-333">TABLE_NAME</span></span>|<span data-ttu-id="cbc84-334">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-334">String</span></span>|  
|<span data-ttu-id="cbc84-335">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="cbc84-335">TABLE_TYPE</span></span>|<span data-ttu-id="cbc84-336">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-336">String</span></span>|  
|<span data-ttu-id="cbc84-337">REMARKS</span><span class="sxs-lookup"><span data-stu-id="cbc84-337">REMARKS</span></span>|<span data-ttu-id="cbc84-338">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-338">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="cbc84-339">列</span><span class="sxs-lookup"><span data-stu-id="cbc84-339">Columns</span></span>  
  
|<span data-ttu-id="cbc84-340">ColumnName</span><span class="sxs-lookup"><span data-stu-id="cbc84-340">ColumnName</span></span>|<span data-ttu-id="cbc84-341">DataType</span><span class="sxs-lookup"><span data-stu-id="cbc84-341">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="cbc84-342">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="cbc84-342">TABLE_QUALIFIER</span></span>|<span data-ttu-id="cbc84-343">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-343">String</span></span>|  
|<span data-ttu-id="cbc84-344">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="cbc84-344">TABLE_OWNER</span></span>|<span data-ttu-id="cbc84-345">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-345">String</span></span>|  
|<span data-ttu-id="cbc84-346">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="cbc84-346">TABLE_NAME</span></span>|<span data-ttu-id="cbc84-347">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-347">String</span></span>|  
|<span data-ttu-id="cbc84-348">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="cbc84-348">COLUMN_NAME</span></span>|<span data-ttu-id="cbc84-349">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-349">String</span></span>|  
|<span data-ttu-id="cbc84-350">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="cbc84-350">DATA_TYPE</span></span>|<span data-ttu-id="cbc84-351">Int16</span><span class="sxs-lookup"><span data-stu-id="cbc84-351">Int16</span></span>|  
|<span data-ttu-id="cbc84-352">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="cbc84-352">TYPE_NAME</span></span>|<span data-ttu-id="cbc84-353">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-353">String</span></span>|  
|<span data-ttu-id="cbc84-354">PRECISION</span><span class="sxs-lookup"><span data-stu-id="cbc84-354">PRECISION</span></span>|<span data-ttu-id="cbc84-355">Int32</span><span class="sxs-lookup"><span data-stu-id="cbc84-355">Int32</span></span>|  
|<span data-ttu-id="cbc84-356">LENGTH</span><span class="sxs-lookup"><span data-stu-id="cbc84-356">LENGTH</span></span>|<span data-ttu-id="cbc84-357">Int32</span><span class="sxs-lookup"><span data-stu-id="cbc84-357">Int32</span></span>|  
|<span data-ttu-id="cbc84-358">SCALE</span><span class="sxs-lookup"><span data-stu-id="cbc84-358">SCALE</span></span>|<span data-ttu-id="cbc84-359">Int16</span><span class="sxs-lookup"><span data-stu-id="cbc84-359">Int16</span></span>|  
|<span data-ttu-id="cbc84-360">RADIX</span><span class="sxs-lookup"><span data-stu-id="cbc84-360">RADIX</span></span>|<span data-ttu-id="cbc84-361">Int16</span><span class="sxs-lookup"><span data-stu-id="cbc84-361">Int16</span></span>|  
|<span data-ttu-id="cbc84-362">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="cbc84-362">NULLABLE</span></span>|<span data-ttu-id="cbc84-363">Int16</span><span class="sxs-lookup"><span data-stu-id="cbc84-363">Int16</span></span>|  
|<span data-ttu-id="cbc84-364">REMARKS</span><span class="sxs-lookup"><span data-stu-id="cbc84-364">REMARKS</span></span>|<span data-ttu-id="cbc84-365">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-365">String</span></span>|  
|<span data-ttu-id="cbc84-366">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="cbc84-366">ORDINAL_POSITION</span></span>|<span data-ttu-id="cbc84-367">Int32</span><span class="sxs-lookup"><span data-stu-id="cbc84-367">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="cbc84-368">手順</span><span class="sxs-lookup"><span data-stu-id="cbc84-368">Procedures</span></span>  
  
|<span data-ttu-id="cbc84-369">ColumnName</span><span class="sxs-lookup"><span data-stu-id="cbc84-369">ColumnName</span></span>|<span data-ttu-id="cbc84-370">DataType</span><span class="sxs-lookup"><span data-stu-id="cbc84-370">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="cbc84-371">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="cbc84-371">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="cbc84-372">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-372">String</span></span>|  
|<span data-ttu-id="cbc84-373">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="cbc84-373">PROCEDURE_OWNER</span></span>|<span data-ttu-id="cbc84-374">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-374">String</span></span>|  
|<span data-ttu-id="cbc84-375">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="cbc84-375">PROCEDURE_NAME</span></span>|<span data-ttu-id="cbc84-376">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-376">String</span></span>|  
|<span data-ttu-id="cbc84-377">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="cbc84-377">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="cbc84-378">Int16</span><span class="sxs-lookup"><span data-stu-id="cbc84-378">Int16</span></span>|  
|<span data-ttu-id="cbc84-379">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="cbc84-379">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="cbc84-380">Int16</span><span class="sxs-lookup"><span data-stu-id="cbc84-380">Int16</span></span>|  
|<span data-ttu-id="cbc84-381">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="cbc84-381">NUM_RESULT_SETS</span></span>|<span data-ttu-id="cbc84-382">Int16</span><span class="sxs-lookup"><span data-stu-id="cbc84-382">Int16</span></span>|  
|<span data-ttu-id="cbc84-383">REMARKS</span><span class="sxs-lookup"><span data-stu-id="cbc84-383">REMARKS</span></span>|<span data-ttu-id="cbc84-384">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-384">String</span></span>|  
|<span data-ttu-id="cbc84-385">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="cbc84-385">PROCEDURE_TYPE</span></span>|<span data-ttu-id="cbc84-386">Int16</span><span class="sxs-lookup"><span data-stu-id="cbc84-386">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="cbc84-387">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="cbc84-387">ProcedureColumns</span></span>  
  
|<span data-ttu-id="cbc84-388">ColumnName</span><span class="sxs-lookup"><span data-stu-id="cbc84-388">ColumnName</span></span>|<span data-ttu-id="cbc84-389">DataType</span><span class="sxs-lookup"><span data-stu-id="cbc84-389">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="cbc84-390">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="cbc84-390">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="cbc84-391">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-391">String</span></span>|  
|<span data-ttu-id="cbc84-392">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="cbc84-392">PROCEDURE_OWNER</span></span>|<span data-ttu-id="cbc84-393">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-393">String</span></span>|  
|<span data-ttu-id="cbc84-394">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="cbc84-394">PROCEDURE_NAME</span></span>|<span data-ttu-id="cbc84-395">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-395">String</span></span>|  
|<span data-ttu-id="cbc84-396">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="cbc84-396">COLUMN_NAME</span></span>|<span data-ttu-id="cbc84-397">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-397">String</span></span>|  
|<span data-ttu-id="cbc84-398">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="cbc84-398">COLUMN_TYPE</span></span>|<span data-ttu-id="cbc84-399">Int16</span><span class="sxs-lookup"><span data-stu-id="cbc84-399">Int16</span></span>|  
|<span data-ttu-id="cbc84-400">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="cbc84-400">DATA_TYPE</span></span>|<span data-ttu-id="cbc84-401">Int16</span><span class="sxs-lookup"><span data-stu-id="cbc84-401">Int16</span></span>|  
|<span data-ttu-id="cbc84-402">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="cbc84-402">TYPE_NAME</span></span>|<span data-ttu-id="cbc84-403">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-403">String</span></span>|  
|<span data-ttu-id="cbc84-404">PRECISION</span><span class="sxs-lookup"><span data-stu-id="cbc84-404">PRECISION</span></span>|<span data-ttu-id="cbc84-405">Int32</span><span class="sxs-lookup"><span data-stu-id="cbc84-405">Int32</span></span>|  
|<span data-ttu-id="cbc84-406">LENGTH</span><span class="sxs-lookup"><span data-stu-id="cbc84-406">LENGTH</span></span>|<span data-ttu-id="cbc84-407">Int32</span><span class="sxs-lookup"><span data-stu-id="cbc84-407">Int32</span></span>|  
|<span data-ttu-id="cbc84-408">SCALE</span><span class="sxs-lookup"><span data-stu-id="cbc84-408">SCALE</span></span>|<span data-ttu-id="cbc84-409">Int16</span><span class="sxs-lookup"><span data-stu-id="cbc84-409">Int16</span></span>|  
|<span data-ttu-id="cbc84-410">RADIX</span><span class="sxs-lookup"><span data-stu-id="cbc84-410">RADIX</span></span>|<span data-ttu-id="cbc84-411">Int16</span><span class="sxs-lookup"><span data-stu-id="cbc84-411">Int16</span></span>|  
|<span data-ttu-id="cbc84-412">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="cbc84-412">NULLABLE</span></span>|<span data-ttu-id="cbc84-413">Int16</span><span class="sxs-lookup"><span data-stu-id="cbc84-413">Int16</span></span>|  
|<span data-ttu-id="cbc84-414">REMARKS</span><span class="sxs-lookup"><span data-stu-id="cbc84-414">REMARKS</span></span>|<span data-ttu-id="cbc84-415">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-415">String</span></span>|  
|<span data-ttu-id="cbc84-416">OVERLOAD</span><span class="sxs-lookup"><span data-stu-id="cbc84-416">OVERLOAD</span></span>|<span data-ttu-id="cbc84-417">Int32</span><span class="sxs-lookup"><span data-stu-id="cbc84-417">Int32</span></span>|  
|<span data-ttu-id="cbc84-418">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="cbc84-418">ORDINAL_POSITION</span></span>|<span data-ttu-id="cbc84-419">Int32</span><span class="sxs-lookup"><span data-stu-id="cbc84-419">Int32</span></span>|  
  
## <a name="microsoft-jet-odbc-driver"></a><span data-ttu-id="cbc84-420">Microsoft Jet ODBC Driver</span><span class="sxs-lookup"><span data-stu-id="cbc84-420">Microsoft Jet ODBC Driver</span></span>  
 <span data-ttu-id="cbc84-421">Microsoft Jet ODBC Driver は、共通のスキーマ コレクションに加えて次のスキーマ コレクションをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="cbc84-421">The Microsoft Jet ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="cbc84-422">[テーブル]</span><span class="sxs-lookup"><span data-stu-id="cbc84-422">Tables</span></span>  
  
-   <span data-ttu-id="cbc84-423">Indexes</span><span class="sxs-lookup"><span data-stu-id="cbc84-423">Indexes</span></span>  
  
-   <span data-ttu-id="cbc84-424">列</span><span class="sxs-lookup"><span data-stu-id="cbc84-424">Columns</span></span>  
  
-   <span data-ttu-id="cbc84-425">手順</span><span class="sxs-lookup"><span data-stu-id="cbc84-425">Procedures</span></span>  
  
-   <span data-ttu-id="cbc84-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="cbc84-426">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="cbc84-427">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="cbc84-427">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="cbc84-428">ビュー</span><span class="sxs-lookup"><span data-stu-id="cbc84-428">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="cbc84-429">Tables と Views</span><span class="sxs-lookup"><span data-stu-id="cbc84-429">Tables and Views</span></span>  
  
|<span data-ttu-id="cbc84-430">ColumnName</span><span class="sxs-lookup"><span data-stu-id="cbc84-430">ColumnName</span></span>|<span data-ttu-id="cbc84-431">DataType</span><span class="sxs-lookup"><span data-stu-id="cbc84-431">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="cbc84-432">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="cbc84-432">TABLE_QUALIFIER</span></span>|<span data-ttu-id="cbc84-433">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-433">String</span></span>|  
|<span data-ttu-id="cbc84-434">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="cbc84-434">TABLE_OWNER</span></span>|<span data-ttu-id="cbc84-435">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-435">String</span></span>|  
|<span data-ttu-id="cbc84-436">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="cbc84-436">TABLE_NAME</span></span>|<span data-ttu-id="cbc84-437">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-437">String</span></span>|  
|<span data-ttu-id="cbc84-438">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="cbc84-438">TABLE_TYPE</span></span>|<span data-ttu-id="cbc84-439">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-439">String</span></span>|  
|<span data-ttu-id="cbc84-440">REMARKS</span><span class="sxs-lookup"><span data-stu-id="cbc84-440">REMARKS</span></span>|<span data-ttu-id="cbc84-441">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-441">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="cbc84-442">列</span><span class="sxs-lookup"><span data-stu-id="cbc84-442">Columns</span></span>  
  
|<span data-ttu-id="cbc84-443">ColumnName</span><span class="sxs-lookup"><span data-stu-id="cbc84-443">ColumnName</span></span>|<span data-ttu-id="cbc84-444">DataType</span><span class="sxs-lookup"><span data-stu-id="cbc84-444">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="cbc84-445">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="cbc84-445">TABLE_QUALIFIER</span></span>|<span data-ttu-id="cbc84-446">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-446">String</span></span>|  
|<span data-ttu-id="cbc84-447">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="cbc84-447">TABLE_OWNER</span></span>|<span data-ttu-id="cbc84-448">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-448">String</span></span>|  
|<span data-ttu-id="cbc84-449">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="cbc84-449">TABLE_NAME</span></span>|<span data-ttu-id="cbc84-450">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-450">String</span></span>|  
|<span data-ttu-id="cbc84-451">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="cbc84-451">COLUMN_NAME</span></span>|<span data-ttu-id="cbc84-452">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-452">String</span></span>|  
|<span data-ttu-id="cbc84-453">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="cbc84-453">DATA_TYPE</span></span>|<span data-ttu-id="cbc84-454">Int16</span><span class="sxs-lookup"><span data-stu-id="cbc84-454">Int16</span></span>|  
|<span data-ttu-id="cbc84-455">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="cbc84-455">TYPE_NAME</span></span>|<span data-ttu-id="cbc84-456">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-456">String</span></span>|  
|<span data-ttu-id="cbc84-457">PRECISION</span><span class="sxs-lookup"><span data-stu-id="cbc84-457">PRECISION</span></span>|<span data-ttu-id="cbc84-458">Int32</span><span class="sxs-lookup"><span data-stu-id="cbc84-458">Int32</span></span>|  
|<span data-ttu-id="cbc84-459">LENGTH</span><span class="sxs-lookup"><span data-stu-id="cbc84-459">LENGTH</span></span>|<span data-ttu-id="cbc84-460">Int32</span><span class="sxs-lookup"><span data-stu-id="cbc84-460">Int32</span></span>|  
|<span data-ttu-id="cbc84-461">SCALE</span><span class="sxs-lookup"><span data-stu-id="cbc84-461">SCALE</span></span>|<span data-ttu-id="cbc84-462">Int16</span><span class="sxs-lookup"><span data-stu-id="cbc84-462">Int16</span></span>|  
|<span data-ttu-id="cbc84-463">RADIX</span><span class="sxs-lookup"><span data-stu-id="cbc84-463">RADIX</span></span>|<span data-ttu-id="cbc84-464">Int16</span><span class="sxs-lookup"><span data-stu-id="cbc84-464">Int16</span></span>|  
|<span data-ttu-id="cbc84-465">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="cbc84-465">NULLABLE</span></span>|<span data-ttu-id="cbc84-466">Int16</span><span class="sxs-lookup"><span data-stu-id="cbc84-466">Int16</span></span>|  
|<span data-ttu-id="cbc84-467">REMARKS</span><span class="sxs-lookup"><span data-stu-id="cbc84-467">REMARKS</span></span>|<span data-ttu-id="cbc84-468">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-468">String</span></span>|  
|<span data-ttu-id="cbc84-469">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="cbc84-469">ORDINAL_POSITION</span></span>|<span data-ttu-id="cbc84-470">Int32</span><span class="sxs-lookup"><span data-stu-id="cbc84-470">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="cbc84-471">手順</span><span class="sxs-lookup"><span data-stu-id="cbc84-471">Procedures</span></span>  
  
|<span data-ttu-id="cbc84-472">ColumnName</span><span class="sxs-lookup"><span data-stu-id="cbc84-472">ColumnName</span></span>|<span data-ttu-id="cbc84-473">DataType</span><span class="sxs-lookup"><span data-stu-id="cbc84-473">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="cbc84-474">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="cbc84-474">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="cbc84-475">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-475">String</span></span>|  
|<span data-ttu-id="cbc84-476">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="cbc84-476">PROCEDURE_OWNER</span></span>|<span data-ttu-id="cbc84-477">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-477">String</span></span>|  
|<span data-ttu-id="cbc84-478">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="cbc84-478">PROCEDURE_NAME</span></span>|<span data-ttu-id="cbc84-479">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-479">String</span></span>|  
|<span data-ttu-id="cbc84-480">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="cbc84-480">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="cbc84-481">Int16</span><span class="sxs-lookup"><span data-stu-id="cbc84-481">Int16</span></span>|  
|<span data-ttu-id="cbc84-482">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="cbc84-482">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="cbc84-483">Int16</span><span class="sxs-lookup"><span data-stu-id="cbc84-483">Int16</span></span>|  
|<span data-ttu-id="cbc84-484">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="cbc84-484">NUM_RESULT_SETS</span></span>|<span data-ttu-id="cbc84-485">Int16</span><span class="sxs-lookup"><span data-stu-id="cbc84-485">Int16</span></span>|  
|<span data-ttu-id="cbc84-486">REMARKS</span><span class="sxs-lookup"><span data-stu-id="cbc84-486">REMARKS</span></span>|<span data-ttu-id="cbc84-487">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-487">String</span></span>|  
|<span data-ttu-id="cbc84-488">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="cbc84-488">PROCEDURE_TYPE</span></span>|<span data-ttu-id="cbc84-489">Int16</span><span class="sxs-lookup"><span data-stu-id="cbc84-489">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="cbc84-490">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="cbc84-490">ProcedureColumns</span></span>  
  
|<span data-ttu-id="cbc84-491">ColumnName</span><span class="sxs-lookup"><span data-stu-id="cbc84-491">ColumnName</span></span>|<span data-ttu-id="cbc84-492">DataType</span><span class="sxs-lookup"><span data-stu-id="cbc84-492">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="cbc84-493">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="cbc84-493">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="cbc84-494">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-494">String</span></span>|  
|<span data-ttu-id="cbc84-495">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="cbc84-495">PROCEDURE_OWNER</span></span>|<span data-ttu-id="cbc84-496">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-496">String</span></span>|  
|<span data-ttu-id="cbc84-497">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="cbc84-497">PROCEDURE_NAME</span></span>|<span data-ttu-id="cbc84-498">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-498">String</span></span>|  
|<span data-ttu-id="cbc84-499">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="cbc84-499">COLUMN_NAME</span></span>|<span data-ttu-id="cbc84-500">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-500">String</span></span>|  
|<span data-ttu-id="cbc84-501">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="cbc84-501">COLUMN_TYPE</span></span>|<span data-ttu-id="cbc84-502">Int16</span><span class="sxs-lookup"><span data-stu-id="cbc84-502">Int16</span></span>|  
|<span data-ttu-id="cbc84-503">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="cbc84-503">DATA_TYPE</span></span>|<span data-ttu-id="cbc84-504">Int16</span><span class="sxs-lookup"><span data-stu-id="cbc84-504">Int16</span></span>|  
|<span data-ttu-id="cbc84-505">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="cbc84-505">TYPE_NAME</span></span>|<span data-ttu-id="cbc84-506">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-506">String</span></span>|  
|<span data-ttu-id="cbc84-507">PRECISION</span><span class="sxs-lookup"><span data-stu-id="cbc84-507">PRECISION</span></span>|<span data-ttu-id="cbc84-508">Int32</span><span class="sxs-lookup"><span data-stu-id="cbc84-508">Int32</span></span>|  
|<span data-ttu-id="cbc84-509">LENGTH</span><span class="sxs-lookup"><span data-stu-id="cbc84-509">LENGTH</span></span>|<span data-ttu-id="cbc84-510">Int32</span><span class="sxs-lookup"><span data-stu-id="cbc84-510">Int32</span></span>|  
|<span data-ttu-id="cbc84-511">SCALE</span><span class="sxs-lookup"><span data-stu-id="cbc84-511">SCALE</span></span>|<span data-ttu-id="cbc84-512">Int16</span><span class="sxs-lookup"><span data-stu-id="cbc84-512">Int16</span></span>|  
|<span data-ttu-id="cbc84-513">RADIX</span><span class="sxs-lookup"><span data-stu-id="cbc84-513">RADIX</span></span>|<span data-ttu-id="cbc84-514">Int16</span><span class="sxs-lookup"><span data-stu-id="cbc84-514">Int16</span></span>|  
|<span data-ttu-id="cbc84-515">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="cbc84-515">NULLABLE</span></span>|<span data-ttu-id="cbc84-516">Int16</span><span class="sxs-lookup"><span data-stu-id="cbc84-516">Int16</span></span>|  
|<span data-ttu-id="cbc84-517">REMARKS</span><span class="sxs-lookup"><span data-stu-id="cbc84-517">REMARKS</span></span>|<span data-ttu-id="cbc84-518">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-518">String</span></span>|  
|<span data-ttu-id="cbc84-519">OVERLOAD</span><span class="sxs-lookup"><span data-stu-id="cbc84-519">OVERLOAD</span></span>|<span data-ttu-id="cbc84-520">Int32</span><span class="sxs-lookup"><span data-stu-id="cbc84-520">Int32</span></span>|  
|<span data-ttu-id="cbc84-521">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="cbc84-521">ORDINAL_POSITION</span></span>|<span data-ttu-id="cbc84-522">Int32</span><span class="sxs-lookup"><span data-stu-id="cbc84-522">Int32</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="cbc84-523">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="cbc84-523">ProcedureParameters</span></span>  
  
|<span data-ttu-id="cbc84-524">ColumnName</span><span class="sxs-lookup"><span data-stu-id="cbc84-524">ColumnName</span></span>|<span data-ttu-id="cbc84-525">DataType</span><span class="sxs-lookup"><span data-stu-id="cbc84-525">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="cbc84-526">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="cbc84-526">PROCEDURE_CAT</span></span>|<span data-ttu-id="cbc84-527">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-527">String</span></span>|  
|<span data-ttu-id="cbc84-528">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="cbc84-528">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="cbc84-529">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-529">String</span></span>|  
|<span data-ttu-id="cbc84-530">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="cbc84-530">PROCEDURE_NAME</span></span>|<span data-ttu-id="cbc84-531">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-531">String</span></span>|  
|<span data-ttu-id="cbc84-532">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="cbc84-532">COLUMN_NAME</span></span>|<span data-ttu-id="cbc84-533">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-533">String</span></span>|  
|<span data-ttu-id="cbc84-534">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="cbc84-534">COLUMN_TYPE</span></span>|<span data-ttu-id="cbc84-535">Int16</span><span class="sxs-lookup"><span data-stu-id="cbc84-535">Int16</span></span>|  
|<span data-ttu-id="cbc84-536">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="cbc84-536">DATA_TYPE</span></span>|<span data-ttu-id="cbc84-537">Int16</span><span class="sxs-lookup"><span data-stu-id="cbc84-537">Int16</span></span>|  
|<span data-ttu-id="cbc84-538">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="cbc84-538">TYPE_NAME</span></span>|<span data-ttu-id="cbc84-539">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-539">String</span></span>|  
|<span data-ttu-id="cbc84-540">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="cbc84-540">COLUMN_SIZE</span></span>|<span data-ttu-id="cbc84-541">Int32</span><span class="sxs-lookup"><span data-stu-id="cbc84-541">Int32</span></span>|  
|<span data-ttu-id="cbc84-542">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="cbc84-542">BUFFER_LENGTH</span></span>|<span data-ttu-id="cbc84-543">Int32</span><span class="sxs-lookup"><span data-stu-id="cbc84-543">Int32</span></span>|  
|<span data-ttu-id="cbc84-544">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="cbc84-544">DECIMAL_DIGITS</span></span>|<span data-ttu-id="cbc84-545">Int16</span><span class="sxs-lookup"><span data-stu-id="cbc84-545">Int16</span></span>|  
|<span data-ttu-id="cbc84-546">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="cbc84-546">NUM_PREC_RADIX</span></span>|<span data-ttu-id="cbc84-547">Int16</span><span class="sxs-lookup"><span data-stu-id="cbc84-547">Int16</span></span>|  
|<span data-ttu-id="cbc84-548">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="cbc84-548">NULLABLE</span></span>|<span data-ttu-id="cbc84-549">Int16</span><span class="sxs-lookup"><span data-stu-id="cbc84-549">Int16</span></span>|  
|<span data-ttu-id="cbc84-550">REMARKS</span><span class="sxs-lookup"><span data-stu-id="cbc84-550">REMARKS</span></span>|<span data-ttu-id="cbc84-551">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-551">String</span></span>|  
|<span data-ttu-id="cbc84-552">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="cbc84-552">COLUMN_DEF</span></span>|<span data-ttu-id="cbc84-553">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-553">String</span></span>|  
|<span data-ttu-id="cbc84-554">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="cbc84-554">SQL_DATA_TYPE</span></span>|<span data-ttu-id="cbc84-555">Int16</span><span class="sxs-lookup"><span data-stu-id="cbc84-555">Int16</span></span>|  
|<span data-ttu-id="cbc84-556">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="cbc84-556">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="cbc84-557">Int16</span><span class="sxs-lookup"><span data-stu-id="cbc84-557">Int16</span></span>|  
|<span data-ttu-id="cbc84-558">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="cbc84-558">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="cbc84-559">Int32</span><span class="sxs-lookup"><span data-stu-id="cbc84-559">Int32</span></span>|  
|<span data-ttu-id="cbc84-560">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="cbc84-560">ORDINAL_POSITION</span></span>|<span data-ttu-id="cbc84-561">Int32</span><span class="sxs-lookup"><span data-stu-id="cbc84-561">Int32</span></span>|  
|<span data-ttu-id="cbc84-562">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="cbc84-562">IS_NULLABLE</span></span>|<span data-ttu-id="cbc84-563">String</span><span class="sxs-lookup"><span data-stu-id="cbc84-563">String</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cbc84-564">参照</span><span class="sxs-lookup"><span data-stu-id="cbc84-564">See Also</span></span>  
 [<span data-ttu-id="cbc84-565">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="cbc84-565">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
