pipeline {
    agent any
    stages {
        stage('Checkout Code') {
            steps {
                echo '✅ 拉取代码，包含测试用TXT文件'
                checkout scm
            }
        }
        stage('Verify TXT File') {
            steps {
                echo '🔍 验证TXT文件存在'
                script {
                    if (fileExists('test.txt')) {
                        echo '✅ 找到测试TXT文件，内容如下：'
                        // 读取并打印TXT内容
                        def content = readFile 'test.txt'
                        echo "${content}"
                    } else {
                        error "❌ 未找到test.txt文件，流程失败"
                    }
                }
            }
        }
        stage('Test CI/CD Pipeline') {
            steps {
                echo '🚀 流程测试进行中'
                // 简单模拟构建步骤：生成新的测试文件
                sh 'echo "CI/CD流程测试成功！构建时间：$(date)" > build_result.txt'
            }
        }
        stage('Finish Test') {
            steps {
                echo '✅ 测试流程完成'
            }
        }
    }
    post {
        success {
            echo '🎉 整个CI/CD测试流程执行成功！'
        }
        failure {
            echo '❌ 测试流程执行失败，请检查配置'
        }
    }
}
