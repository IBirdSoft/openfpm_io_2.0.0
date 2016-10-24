#!groovy

parallel (

"nyu" : {node ('nyu')
                  {
                    deleteDir()
                    checkout scm
                    stage ('build_nyu')
                    {
                      sh "./build.sh $WORKSPACE $NODE_NAME"
                    }

                    stage ('run_nyu')
                    {
                      sh "cd openfpm_io && ./run.sh $WORKSPACE $NODE_NAME"
                    }
                  }
                 },


"sb15" : {node ('sbalzarini-mac-15')
                  {
                    deleteDir()
                    env.PATH = "/usr/local/bin:${env.PATH}"
                    checkout scm
                    stage ('build_sb15')
                    {
                      sh "echo $PATH && ./build.sh $WORKSPACE $NODE_NAME"
                    }

                    stage ('run_sb15_val')
                    {
                      sh "cd openfpm_io && ./run.sh $WORKSPACE $NODE_NAME"
                    }
                  }
                 },

"gin" : {node ('gin')
                  {
                    deleteDir()
                    checkout scm
                    stage ('build_gin')
                    {
                      sh "echo $PATH && ./build.sh $WORKSPACE $NODE_NAME"
                    }

                    stage ('run_gin')
                    {
                      sh "cd openfpm_io && ./run.sh $WORKSPACE $NODE_NAME"
                    }
                  }
                 }
)
