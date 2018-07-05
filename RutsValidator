=begin
	Script to validate Chilean RUTs
=end

class Rut

  def initialize()

    @rut = String.new

    while @rut.empty?
      puts "Ingresa tu rut, porfavor"
      @rut = gets.chomp
    end

  end

  def toArray

    rut_split = @rut.tr('.','').strip.split("-") #Split the chain, the first one until the char and the second after the char. Remains as string. strip, return a copy of the string without whitespace
    @numero = rut_split.first.reverse #Get the first part of the split and turns in a reverse
    @verificador = rut_split.last #Get the second part of the split
    #puts "second split #{@verificador}"

  end

  def verifica

    serie = []

    numeroChar = @numero.split("").map(&:to_i) #String to int
    #puts "#{numeroChar}"

    if numeroChar.count > 7
      serie = [2,3,4,5,6,7,2,3]
    else
      serie = [2,3,4,5,6,7,2]
    end

    mulArrays = numeroChar.zip(serie).map{|x,y| x*y} #This works because zip combines the two arrays into a single array of two element arrays. i.e.:

    sumArrays = mulArrays.sum #suma los valores del arreglo. Solo ruby 2.4+
    puts sumArrays

    modulo = sumArrays/11 #modulo 11 de la suma de los arreglos
    mul = modulo.to_i*11 #multiplicacion de la parte entera del modulo anterior
    dif = sumArrays-mul  #diferencia
    codigo = 11-dif #codigo verificador
    puts codigo

    if codigo == 11
      codigo = 0
    elsif codigo == 10
      codigo = "k"
    end

    if codigo == @verificador.to_i
      puts "El rut existe"
    else
      puts "El rut no existe"
    end


  end

  attr_accessor :rut

end

objeto = Rut.new
objeto.toArray
objeto.verifica

