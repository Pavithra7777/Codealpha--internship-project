# Codealpha--internship-project
This repository contains my project for internship in codealpha.
// data redundancy removal system 
import { useState } from 'react';
import { Card, CardContent, CardHeader, CardTitle } from '@/components/ui/card';
import { Button } from '@/components/ui/button';
import { Tabs, TabsContent, TabsList, TabsTrigger } from '@/components/ui/tabs';
import { Badge } from '@/components/ui/badge';
import { Alert, AlertDescription } from '@/components/ui/alert';
import { 
  Shield, 
  Database, 
  Upload, 
  BarChart3, 
  Settings,
  AlertTriangle,
  CheckCircle,
  TrendingUp,
  Users,
  FileCheck
} from 'lucide-react';
import { DataValidator } from '@/components/data-validator';
import { DataImport } from '@/components/data-import';
import { Toaster } from '@/components/ui/toaster';
import { mockValidationStats } from '@/data/mock-validation-data';

function App() {
  const [activeTab, setActiveTab] = useState('dashboard');

  return (
    <div className="min-h-screen bg-gray-50">
      <div className="border-b bg-white">
        <div className="max-w-7xl mx-auto px-4 py-4">
          <div className="flex items-center justify-between">
            <div>
              <h1 className="text-2xl font-bold flex items-center gap-2">
                <Shield className="h-6 w-6 text-blue-600" />
                Data Redundancy Removal System
              </h1>
              <p className="text-muted-foreground">
                Intelligent duplicate detection and data validation platform
              </p>
            </div>
            <div className="flex items-center gap-4">
              <Badge variant="outline" className="text-green-600 border-green-600">
                System Active
              </Badge>
              <Button size="sm" variant="outline">
                <Settings className="h-4 w-4 mr-2" />
                Settings
              </Button>
            </div>
          </div>
        </div>
      </div>

      <div className="max-w-7xl mx-auto px-4 py-6">
        <Tabs value={activeTab} onValueChange={setActiveTab} className="space-y-6">
          <TabsList className="grid w-full grid-cols-4">
            <TabsTrigger value="dashboard" className="flex items-center gap-2">
              <BarChart3 className="h-4 w-4" />
              Dashboard
            </TabsTrigger>
            <TabsTrigger value="validation" className="flex items-center gap-2">
              <Shield className="h-4 w-4" />
              Validation
            </TabsTrigger>
            <TabsTrigger value="import" className="flex items-center gap-2">
              <Upload className="h-4 w-4" />
              Data Import
            </TabsTrigger>
            <TabsTrigger value="analytics" className="flex items-center gap-2">
              <TrendingUp className="h-4 w-4" />
              Analytics
            </TabsTrigger>
          </TabsList>

          <TabsContent value="dashboard" className="space-y-6">
            {/* System Overview */}
            <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-4">
<Card>
                <CardContent className="p-6">
                  <div className="flex items-center justify-between">
                    <div>
                      <p className="text-sm text-muted-foreground">Total Records</p>
                      <p className="text-2xl font-bold">{mockValidationStats.totalRecords.toLocaleString()}</p>
                    </div>
                    <Database className="h-8 w-8 text-blue-500" />
                  </div>
                  <p className="text-xs text-muted-foreground mt-2">
                    Across all data sources
                  </p>
                </CardContent>
              </Card>

              <Card>
                <CardContent className="p-6">
                  <div className="flex items-center justify-between">
                    <div>
                      <p className="text-sm text-muted-foreground">Data Quality Score</p>
                      <p className="text-2xl font-bold text-green-600">{mockValidationStats.dataQualityScore}%</p>
                    </div>
                    <FileCheck className="h-8 w-8 text-green-500" />
                  </div>
                  <p className="text-xs text-green-600 mt-2">
                    +2.3% from last month
                  </p>
                </CardContent>
              </Card>

              <Card>
                <CardContent className="p-6">
                  <div className="flex items-center justify-between">
                    <div>
                      <p className="text-sm text-muted-foreground">Duplicates Prevented</p>
                      <p className="text-2xl font-bold text-orange-600">{mockValidationStats.preventedDuplicates}</p>
                    </div>
                    <AlertTriangle className="h-8 w-8 text-orange-500" />
                  </div>
                  <p className="text-xs text-orange-600 mt-2">
                    This month
                  </p>
                </CardContent>
              </Card>

              <Card>
                <CardContent className="p-6">
                  <div className="flex items-center justify-between">
                    <div>
                      <p className="text-sm text-muted-foreground">Active Users</p>
                      <p className="text-2xl font-bold">24</p>
                    </div>
                    <Users className="h-8 w-8 text-purple-500" />
                  </div>
                  <p className="text-xs text-muted-foreground mt-2">
                    Using the system
                  </p>
                </CardContent>
              </Card>
            </div>

            {/* Recent Activity */}
            <div className="grid grid-cols-1 lg:grid-cols-2 gap-6">
              <Card>
                <CardHeader>
                  <CardTitle>Recent Duplicate Detections</CardTitle>
                </CardHeader>
                <CardContent>
                  <div className="space-y-3">
                    <div className="flex items-center justify-between p-3 border rounded-lg">
                      <div>
                        <p className="font-medium">John Smith vs J. Smith</p>
                        <p className="text-sm text-muted-foreground">Email & Phone match</p>
                      </div>
                      <Badge variant="destructive">95.2%</Badge>
                    </div>
                    <div className="flex items- center justify-between p-3 border rounded-lg">
                      <div>
                        <p className="font-medium">Tech Corp vs TechCorp Inc</p>
                        <p className="text-sm text-muted-foreground">Company name similarity</p>
                      </div>
                      <Badge variant="outline">87.6%</Badge>
                    </div>
                    <div className="flex items-center justify-between p-3 border rounded-lg">
                      <div>
                        <p className="font-medium">jane.doe vs j.doe</p>
                        <p className="text-sm text-muted-foreground">Address match</p>
                      </div>
                      <Badge variant="outline">82.1%</Badge>
                    </div>
                  </div>
                </CardContent>
              </Card>

              <Card>
                <CardHeader>
                  <CardTitle>System Alerts</CardTitle>
                </CardHeader>
                <CardContent className="space-y-3">
                  <Alert>
                    <CheckCircle className="h-4 w-4" />
                    <AlertDescription>
                      Data import completed successfully. 1,247 records processed, 23 duplicates detected.
                    </AlertDescription>
                  </Alert>
                  <Alert>
                    <AlertTriangle className="h-4 w-4" />
                    <AlertDescription>
                      High similarity threshold reached. 15 potential duplicates require manual review.
                    </AlertDescription>
                  </Alert>
                  <Alert>
                    <CheckCircle className="h-4 w-4" />
                    <AlertDescription>
                      Validation rules updated. New email format validation is now active.
                    </AlertDescription>
                  </Alert>
                </CardContent>
              </Card>
            </div>

            {/* Performance Metrics */}
            <Card>
              <CardHeader>
                <CardTitle>System Performance</CardTitle>
              </CardHeader>
              <CardContent>
                <div className="grid grid-cols-1 md:grid-cols-3 gap-6">
                  <div className="text-center p-4 border rounded-lg">
                    <div className="text-3xl font-bold text-blue-600">2.3s</div>
                    <p className="text-sm text-muted-foreground">Average validation time</p>
                  </div>
                  <div className="text-center p-4 border rounded-lg">
                    <div className="text-3xl font-bold text-green-600">99.7%</div>
                    <p className="text-sm text-muted-foreground">System uptime</p>
                  </div>
                  <div className="text-center p-4 border rounded-lg">
<div className="text-3xl font-bold text-purple-600">1.2M</div>
                    <p className="text-sm text-muted-foreground">Records processed today</p>
                  </div>
                </div>
              </CardContent>
            </Card>
          </TabsContent>

          <TabsContent value="validation">
            <DataValidator />
          </TabsContent>

          <TabsContent value="import">
            <DataImport />
          </TabsContent>

          <TabsContent value="analytics" className="space-y-6">
            <Card>
              <CardHeader>
                <CardTitle className="flex items-center gap-2">
                  <TrendingUp className="h-5 w-5" />
                  Advanced Analytics
                </CardTitle>
              </CardHeader>
              <CardContent>
                <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-4">
                  <div className="text-center p-4 border rounded-lg">
                    <div className="text-2xl font-bold text-green-600">
                      {((mockValidationStats.validRecords / mockValidationStats.totalRecords) * 100).toFixed(1)}%
                    </div>
                    <p className="text-sm text-muted-foreground">Clean Data Rate</p>
                  </div>
                  <div className="text-center p-4 border rounded-lg">
                    <div className="text-2xl font-bold text-orange-600">
                      {((mockValidationStats.duplicateRecords / mockValidationStats.totalRecords) * 100).toFixed(1)}%
                    </div>
                    <p className="text-sm text-muted-foreground">Duplicate Rate</p>
                  </div>
                  <div className="text-center p-4 border rounded-lg">
                    <div className="text-2xl font-bold text-red-600">
                      {((mockValidationStats.falsePositives / mockValidationStats.duplicateRecords) * 100).toFixed(1)}%
                    </div>
                    <p className="text-sm text-muted-foreground">False Positive Rate</p>
                  </div>
                  <div className="text-center p-4 border rounded-lg">
                    <div className="text-2xl font-bold text-blue-600">
                      ${((mockValidationStats.preventedDuplicates * 150) / 1000).toFixed(0)}K
                    </div>
                    <p className="text-sm text-muted-foreground">Cost Savings</p>
                  </div>
                </div>
              </CardContent>
            </Card>

            <Card>
              <CardHeader>
                <CardTitle>Trend Analysis</CardTitle>
              </CardHeader>
              <CardContent>
                <div className="h-64 bg-gray-50 rounded-lg flex items-center justify-center">
                  <div className="text-center text-muted-foreground">
                    <BarChart3 className="h-12 w-12 mx-auto mb-2" />
                    <div className="text-lg font-medium">Trend Charts</div>
                    <div className="text-sm">Data quality trends over time would be displayed here</div>
                  </div>
                </div>
              </CardContent>
            </Card>
          </TabsContent>
        </Tabs>
      </div>

      <Toaster />
    </div>
  );
}

export default App;
