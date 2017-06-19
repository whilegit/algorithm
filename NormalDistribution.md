正态分布算法 Normal Distribution
============
# 获取符合正态分布的随机数
> 本例使用java书写

    public double getNd(double expect, double std_dev){
        return expect + randomNd() * std_dev;
    } 
    
    private double randomNd(){
        double u=0.0, v=0.0, w=0.0, c=0.0;
        do{
            //获取两个(-1,1)区间的独立随机变量
            u = Math.random() * 2 - 1.0;
            v = Math.random() * 2 - 1.0;
            w = u * u + v * v;
        } while(w == 0.0 || w >= 1.0);
        //Box-muller转换
        c = Math.sqrt((-2 * Math.log(w))/w);
        // u*c 和v * c 都符合正态分布要求,这里选取一个就可以了
        return u*c;
    }

