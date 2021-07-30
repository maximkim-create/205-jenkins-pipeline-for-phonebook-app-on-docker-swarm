resource "aws_instance" "apache-server" {
  ami             = data.aws_ami.amazon-linux-2.id
  instance_type   = "t2.micro"
  key_name        = "Second"
  count           = 2
  security_groups = ["tf-project"]
  user_data = file("create_apache.sh")

  tags = {
    Name = "terraform ${element(var.mytags, count.index)} instance"
  }
    provisioner "local-exec" {
      command = "echo ${self.private_ip} >> private_ip.txt"
    }
    provisioner "local-exec" {
      command = "echo ${self.public_ip} >> public_ip.txt"
    }
}